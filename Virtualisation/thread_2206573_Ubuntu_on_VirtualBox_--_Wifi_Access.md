---
title: "Ubuntu on VirtualBox -- Wifi Access"
date: 2014-02-19
forum: Virtualisation
---

### Post by drivingmemad on 2014-02-19
OK. Ive got VirtualBox 4.3.6 r91406 installed on Windows 7 Professional
Laptop is a HP Pavillion G Series with a Ralink RT5390 802.11b/g WiFi Adaptor
Ive created a virtual Ubuntu 12.04.3 LTS installation in VirtualBox, but cannot seem to get the VM to connect wirelessly.
Ive tried all of the configurations of virtual network adaptors in Vbox, but nothing has worked.
Ive had a similar problem on a physical computer with Ubuntu and resolved it by loading the B43 module using "modprobe B43" and appending B43 to /etc/modules. Unfortunately that computer is now dead, hence VBox.
On the virtual Ubuntu installation I have tried the steps mentioned above:-
modprobe B43
appended B43 to /etc/modules
Tried all the different virtual network adaptors in VBox.
All to no avail.
If anyone can provide any guidance, that would be fantastic.

Regards,
drivingmemad

---

### Post by SeijiSensei on 2014-02-19
First of all, the VMs don't see the actual network adapter, they see an emulated version of the Intel E1000 gigabit adapter.

If you chose NAT as the network model, everything should work flawlessly once the Windows host is connected to the network.  You shouldn't need to add any additional drivers.  You won't be able to see the VM from outside the host machine in this arrangement, but you certainly should be able to browse outbound on the Internet.

With NAT enabled, run the command "ifconfig".  You should see an entry for eth0 (the emulated network adapter) with an address like 10.x.x.x.

---

### Post by drivingmemad on 2014-02-20
hi SeijiSensei,
Thanks for the response. I will give this a try tonight when Im at home and will report back :-)

---

### Post by drivingmemad on 2014-02-20
OK. So that didnt work unfortunately.
I selected NAT in the Attached To: box in Network settings
Then Ive selected each of the Adapter Types 1 by 1 under Advanced settings 
Each time I boot into Ubuntu I dont get connected to the internet.
When i click on the network indicator along the top it says "Wired Network"
I dont want wired i want wireless.

drivingmemad

---

### Post by IvoGuerreiro on 2014-02-21
I was searching and see this link below, i think that can really help.
[http://askubuntu.com/questions/282018/wifi-card-on-an-virtualboxs-ubuntu](http://askubuntu.com/questions/282018/wifi-card-on-an-virtualboxs-ubuntu)

---

### Post by drivingmemad on 2014-02-21
Thanks IvoGuerreiro
the version of VirtualBox I have installed already has the Addons
I did an ifconfig and I dont see a wlan0 on my virtual ubuntu
Any other ideas, please

---

### Post by SeijiSensei on 2014-02-21
The virtual machine will not use the wifi interface.  The Windows host is using that already.  The guest VM connects to the host over an emulated Ethernet connection.  When the VM comes up in NAT mode, it should have assigned an address to eth0, usually something like 10.8.0.2.  The host has an equivalent emulated adapter to which the VM talks.  Packets from the VM intended for the Internet go first through this emulated network to the host which retransmits them out the actual wifi interface.

Have you read the user manual for VirtualBox, in particular the [section on networking]("https://www.virtualbox.org/manual/ch06.html")?

---

### Post by drivingmemad on 2014-02-22
Ive read the section on networking, even though I had already tried the NAT selection in "Attached To", then, Adapter Type: PCnet-FAST III (Am79c973) on previous attempts. However, I have now done this again. Once the virtual OS has boot up I get a message "Disconnected - you are now offline"
In the networking pages for virtualbox I saw the command to start the natnetwork service. Thinking this may be the resolution i need, I tried it:

<terminal output>
root@user-VirtualBox:/home/user/#VBoxManage natnetwork start -t nat-int-network
The program 'VBoxManage' is currently not installed. You can install it by typing:
apt-get install VirtualBox
</terminal output>
Except I cannot do the apt-get because i cant get an internet connection.
Sorry for sounding vague here, but why would I need to install VirtualBox on a VirtualBox 
virtual machine?

---

### Post by drivingmemad on 2014-02-25
Does anyone else have any insight into this one. It is possible I may be misunderstanding the documentation, but I feel like ive checked everything and have definitely tried all the different network settings in VBox. Could i have misconfigured something in the Ubuntu VM could somebody advise where to check. Ive done modprobe B43 to get that module loading on start up. Ive also appended B43 to /etc/modules. Should i have done that?
Is there something else I have missed?

drivingmemad

---

### Post by SeijiSensei on 2014-02-25
As I said, you don't need the b43 driver because the VM never sees the wifi device.

Boot up the virtual machine, then run "ifconfig" from a command prompt.  What interfaces do you see?  Usually, in the default NAT mode, VirtualBox will assign 10.0.2.15 to the guest's virtual interface and 10.0.2.2 to the virtual interface on the host.  If you run the command "route -n" you should see that the guest's default gateway is 10.0.2.2.  Try pinging 10.0.2.2.  If you cannot do that, something is not configured correctly.

Frankly I would suggest erasing your current installation of VBox and reinstalling, or create a new virtual machine.  By now you've probably tried so many different things that it would be hard to determine where the problem might lie.

---

### Post by drivingmemad on 2014-02-25
ifconfig shows me the MAC address that VBox shows in network settings, but no IP Address
route -n gives me nothing at all
will completely remove/reinstall vbox as you have suggested.
Thanks for the reponse :-)

---

