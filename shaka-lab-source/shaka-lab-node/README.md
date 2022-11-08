# Shaka Lab Node

The Shaka Lab Node package provides Selenium grid nodes, and is available for
[Linux](#linux), [Windows](#windows), and [macOS](#macos).


## Linux

NOTE: Browsers running in a Linux node **will not** be visible.

Installation:

```sh
curl -L https://shaka-project.github.io/shaka-lab/public.key | \
    sudo tee /etc/apt/trusted.gpg.d/shaka-lab.asc
echo deb https://shaka-project.github.io/shaka-lab/ stable main | \
    sudo tee /etc/apt/sources.list.d/shaka-lab.list
sudo apt update
sudo apt install -y shaka-lab-node
```

Updates:

```sh
sudo apt update && sudo apt -y upgrade
```

Configuration:

The config file is at `/etc/shaka-lab-node-config.yaml`.
See the [configuration section](#configuration) below for details.

Restarting the service after editing the config:

```sh
sudo systemctl restart shaka-lab-node
```

Tailing logs:

```sh
journalctl --no-hostname -u shaka-lab-node --follow
```

Uninstallation:

```sh
sudo apt remove shaka-lab-node
```


## Windows

NOTE: Browsers running in a Windows node **will not** be visible.

Pre-requisites:

 - Get Chocolatey: [https://docs.chocolatey.org/en-us/choco/setup](https://docs.chocolatey.org/en-us/choco/setup)

Installation:

```sh
choco source add -n=shaka-lab -s=https://shaka-lab-chocolatey-dot-shaka-player-demo.appspot.com/
choco install shaka-lab-node
```

Updates:

```sh
choco upgrade -y shaka-lab-node
```

Configuration:

The config file is at `c:\ProgramData\shaka-lab-node\node-config.yaml`.
See the [configuration section](#configuration) below for details.

Restarting the service after editing the config:

```sh
net stop shaka-lab-node
net start shaka-lab-node
```

Tailing logs:

```sh
powershell -command "Get-Content c:/ProgramData/shaka-lab-node/logs/shaka-lab-node-svc.err.log -Wait"
```

Uninstallation:

```sh
choco uninstall -y shaka-lab-node
```


## macOS

NOTE: Browsers running in a macOS node **will** be visible.

Pre-requisites:

 - Get Homebrew: [https://brew.sh/#install](https://brew.sh/#install)

Installation:

```sh
brew tap shaka-project/shaka-lab
brew install shaka-lab-node
/opt/homebrew/opt/shaka-lab-node/restart-services.sh
```

Updates:

```sh
brew update && brew upgrade
/opt/homebrew/opt/shaka-lab-node/restart-services.sh
```

Configuration:

The config file is at `/opt/homebrew/etc/shaka-lab-node-config.yaml`.
See the [configuration section](#configuration) below for details.

Restarting the service after editing the config:

```sh
/opt/homebrew/opt/shaka-lab-node/restart-services.sh
```

Tailing logs:

```sh
tail -f /opt/homebrew/var/log/shaka-lab-node.err.log
```

Uninstallation:

```sh
/opt/homebrew/opt/shaka-lab-node/stop-services.sh
brew uninstall shaka-lab-node
```


## Configuration

TODO: Explain node configuration

TODO: Explain debug logging


## Special node setup requirements

 - Browser nodes require those browsers to be separately installed.
 - Tizen nodes require Docker, but can run on any OS.
 - Tizen TVs must be configured to accept commands from the IP of the device
   running the Tizen node.
 - Android nodes require `adb`, but can run on any OS.
 - Xbox One nodes require Visual Studio and must be run on Windows.
