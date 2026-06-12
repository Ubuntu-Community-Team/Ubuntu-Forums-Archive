---
title: "Problems installing docker desktop"
date: 2023-01-21
forum: Virtualisation
---

### Post by javgar on 2023-01-21
Hello Im new to Ubuntu and Im trying to install docker desktop, but when I try, I receive this:[INDENT]$ sudo apt-get install ./docker-desktop-4.16.2-amd64.deb [/INDENT]
[INDENT]Reading package lists... Done[/INDENT]
[INDENT]Building dependency tree       [/INDENT]
[INDENT]Reading state information... Done[/INDENT]
[INDENT]Note, selecting 'docker-desktop' instead of './docker-desktop-4.16.2-amd64.deb'[/INDENT]
[INDENT]Some packages could not be installed. This may mean that you have[/INDENT]
[INDENT]requested an impossible situation or if you are using the unstable[/INDENT]
[INDENT]distribution that some required packages have not yet been created[/INDENT]
[INDENT]or been moved out of Incoming.[/INDENT]
[INDENT]The following information may help to resolve the situation:[/INDENT]
[INDENT]
[/INDENT]
[INDENT]The following packages have unmet dependencies.[/INDENT]
[INDENT] docker-desktop : Depends: qemu-system-x86 (>= 5.2.0) but it is not installable[/INDENT]
[INDENT]E: Unable to correct problems, you have held broken packages.[/INDENT]

If I try to install qemu, I receive this:

$ sudo apt-get -y install qemu-system-x86Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package qemu-system-x86 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  sgabios


E: Package 'qemu-system-x86' has no installation candidate





I installed sgabios, but still can't install Docker Desktop.

Thanks in advance

---

### Post by javgar on 2023-01-21
I have solved it. It was a misconfiguration in software & updates

---

### Post by MAFoElffen on 2023-01-21
There's dependencies that have to be installed and configured before and in the process of...

To install Docker Desktop...
```

sudo apt update
sudo apt install qemu-kvm libvirt-daemon-system virtinst libvirt-clients
sudo systemctl enable libvirtd
sudo systemctl start libvirtd
sudo usermod -aG kvm $USER
sudo usermod -aG libvirt $USER
sudo apt remove docker docker-engine docker.io 2>/dev/null
sudo apt update
sudo apt -y install apt-transport-https ca-certificates curl software-properties-common
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/trusted.gpg.d/docker-archive-keyring.gpg
sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"
sudo apt install docker-ce docker-ce-cli containerd.io uidmap
sudo usermod -aG docker $USER
newgrp docker
wget https://desktop.docker.com/linux/main/amd64/docker-desktop-4.12.0-amd64.deb
sudo apt remove docker-desktop
rm -r $HOME/.docker/desktop
sudo rm /usr/local/bin/com.docker.cli
sudo apt purge docker-desktop
sudo apt install gnome-terminal
sudo apt install ./docker-desktop-*-amd64.deb
systemctl --user start docker-desktop
# Accept License and quit
docker compose version
docker version
sudo systemctl stop docker docker.socket containerd
sudo systemctl disable docker docker.socket containerd
docker context ls
docker context use default
docker context use desktop-linux





```
Configure Docker Desktop...

---

### Post by alert8810 on 2023-01-28
Thanks I have installed docker desktop.  But when I start I get an error:

# systemctl --user start docker-desktop
Failed to connect to bus: $DBUS_SESSION_BUS_ADDRESS and $XDG_RUNTIME_DIR not defined (consider using --machine=<user>@.host --user to connect to bus of other user)

---

### Post by alert8810 on 2023-01-28
helped me

export $(dbus-launch)

---

### Post by sumba2 on 2023-08-20
After reading some documentations on the docker website. I put together this script which successfully installs the docker engine and docker desktop on ubuntu 22.04.I hope this helps resolve your issue
```

# Docker Desktop Installation for ubuntu 22.04
#Update the apt package index and install packages to allow apt to use a repository over HTTPS:
sudo apt-get update
sudo apt-get install ca-certificates curl gnupg
#Add Docker’s official GPG key:
sudo install -m 0755 -d /etc/apt/keyrings
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
sudo chmod a+r /etc/apt/keyrings/docker.gpg
#Use the following command to set up the repository:
#If you use an Ubuntu derivative distro, such as Linux Mint, you may need to use UBUNTU_CODENAME instead of VERSION_CODENAME.

echo \
  "deb [arch="$(dpkg --print-architecture)" signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu \
  "$(. /etc/os-release && echo "$VERSION_CODENAME")" stable" | \
  sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
  #Update the apt package index:
  sudo apt-get update
  #To install the latest version of Docker Engine, run:
  sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
  #Verify that the Docker Engine installation is successful by running the hello-world image
  sudo docker run hello-world
  # Installing Docker Desktop
  # download lastest Debian package to a directory and install from there with the command below
  cd /path to your downloaded file/
  sudo apt-get update
  # install the gemu dependencies very necessary if your previous installation complained about it.
  sudo apt install qemu-kvm libvirt-daemon-system virtinst libvirt-clients
  sudo dpkg -i /path to your downloaded file/docker-desktop-4.22.0-amd64.deb

```

---

