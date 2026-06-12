---
title: "vmware view client linux"
date: 2018-03-07
forum: Ubuntu, Linux and OS Chat
---

### Post by efeliz on 2018-03-07
I'm a beginner using or configuring linux
but this works well for me even customizing an iso

On Lubuntu

apt  install g++ libxml2-dev libboost-dev qt5-default qtbase5-dev-tools  qtdeclarative5-dev libqt5svg5-dev libqt5websockets5-dev git cmake  libportmidi0 libasound2 python

Download VMware-Horizon-Client-*.x86.bundle from vmware page
Then  you can run it from the folder it's downloaded, running this will  install vmware_client ./VMware-Horizon-Client-*.x86.bundle or sh  ./VMware-Horizon-Client-*.x86.bundle


Create vmware.sh 
echo "vmware-view -q --nonInteractive --fullscreen --nomenubar --lockServer -s your_view_server_FQDN.local" > /.vmware.sh

Create others.sh

#this line will void checking for the view sever certificate if no needed don't use it.

echo "echo "view.sslVerificationMode = \"3\"" > /etc/vmware/view-mandatory-config

#this other line adds your view server FQDN to local hosts file you can repeat it if necessary

echo "192.168.1.1 viewservershortname viewserverFQDN.local" >> /etc/hosts"
#this line cleanses the script after it run once, 
echo "" > /.others.sh

It's necesary to give both some permissions I've set 777
chmod 777 ./vmware.sh
chmod 777 ./others.sh

Now you can make those script run, i preferred to make them run automatically the way i did it is

run crontab -e

#there you can write 
@reboot /.others.sh
#save and quit

Edit the file /etc/xdg/lxsession/Lubuntu/autostart
#write this command to autostart the view client automatically
@vmware-view -q --nonInteractive --fullscreen --nomenubar --lockServer -s your_view_server_FQDN.local

Now you can customize your own ubuntu linux vmware view client

P.D. I've used CUBIC to customize the ISO

I've test UCK but didn't work recommend cubic

---

