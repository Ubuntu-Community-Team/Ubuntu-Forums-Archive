---
title: "Autostart/Autoshutdown pihole VM in Virtualbox 5.2.26 running on Ubuntu 18.04.2"
date: 2019-02-19
forum: Virtualisation
---

### Post by benbrockn on 2019-02-19
Alright, this took me several hours to figure out and since I got it working, I'll share with you all how I did it.
The problem was that I couldn't get [this guy's guide]("https://medium.com/@bharatman/how-to-autostart-and-autostop-your-headless-virtualbox-guest-vm-on-a-debian-host-3ca7ede2380b") to work, so I had to tweak it.
There were two issues:
[LIST=1]
[*]It never autostarted upon, well, startup. Syslog kept throwing an error saying: "vboxheadless invalid machine name or uuid" when I knew the name or UUID was correct 
[*]It started ***after*** the network service resulting in many attempts by Ubuntu to try to resolve names to repos, the NTP server, etc... and failing because the pihole DNS wasn't running yet 
[/LIST]

**Setup:**
[LIST]
[*]Linux tower with Ubuntu 18.04.2 LTS 
[*]Virtualbox 5.2.26 installed on that tower 
[*]VM with Ubuntu Server 18.04.2 & pihole 
[/LIST]

**(Skip if you know this) Preliminary Steps on how to set everything up:**
[LIST=1]
[*]Install Virtualbox 5.2.26 by downloading the .deb pkg from the Virtualbox website (the distro's package was older and v6.0 wouldn't load) 
[*]Create a new VM, name it whatever, only 1GB RAM needed 
[*]Add a SATA optical drive, attach the Ubuntu Server 18.04.2 ISO 
[*]Network -> "Bridged Mode", copy the MAC address 
[*]On your router, add that MAC address as a static lease with a new IP address.
[LIST=1]
[*]If you have a DD-WRT router, go to "Services -> Services", add a  static lease for that MAC address you copied earlier, add a new IP  address. Reboot the router and wait for it to come back online. 
[/LIST]
  
[*]Run the VM and Install Ubuntu Server 
[*]Reboot 
[*]Once the server works, install pihole via ```
curl -sSL https://install.pi-hole.net | bash
``` 
[*]Reboot 
[*]Rebuild Gravity via ```
pihole -g -f
``` 
[*]Reboot 
[*]On your router, add in DNS routing to accomodate pihole
[LIST=1]
[*]If you have a DD-WRT router, on "Setup -> Basic Setup" leave "Local DNS" as 0.0.0.0 and "Static DNS 1..3" as 0.0.0.0 
[*]Go to "Services -> Services" and under "Additional DNSMasq Options" add this line: ```
dhcp-option=6,pihole_IP_Address
``` . Yes, there is no space between that comma and the IP address of your pihole you configured earlier 
[/LIST]
  
[*]In the pihole admin console (IP_Address/admin/ **OR** pi.hole/admin/), go to "Settings -> DNS". Leave everything unchecked except under "Custom1 IPv4", add the IP address of your router (aka gateway). 
[/LIST]

**Autostart/Autoshutdown Steps:**
[LIST=1]
[*]Create a txt file on your desktop call it "whatever-vm.service" 
[*]Paste this into your new txt file, where **username** is the name of the user you installed virtualbox/created the VM in, and **machine_name** is the name (or UUID if you prefer) of your pihole VM:
[LIST]
[*]```

[Unit]
Description=pihole VM service
After=vboxdrv.service

[Service]
ExecStart=/sbin/runuser -l **username** -c 'vboxheadless -s **machine_name**'
ExecStop=/sbin/runuser -l **username** -c 'vboxmanage controlvm **machine_name** acpipowerbutton'

[Install]
WantedBy=multi-user.target

``` 
[/LIST]
  
[*]sudo copy that "whatever-vm.service" file into /etc/systemd/system 
[*]Run: ```
systemctl daemon-reload
``` 
[*]Then run this,  where "whatever-vm" is the first part of that .service file you just created: ```
systemctl enable whatever-vm
``` 
[/LIST]


 **Why this code works:**
[LIST=1]
[*]This new service runs as soon as the main vboxdrv.service runs, and doesn't wait for the network to be up (which it can't reach because your pihole DNS isn't running) 
[*]That guy's code in the original article was trying to run the VM as root, when the VM only exists in your local user profile. Since systemd acts as root, it needs to run the virtualbox command as your username for it to actually work. The runuser command fixes this by allowing root to run as the user of your account. 
[/LIST]

Cheers! Hope this helps some people!

---

