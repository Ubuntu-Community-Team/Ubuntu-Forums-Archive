---
title: "mACH7OUT"
date: 2010-01-06
forum: Virtualisation
---

### Post by mach7out on 2010-01-06
Hail!

here's to where i got so far!

am using karmic koala,  got sun virtual box but didnt really work for me, so i downloaded vmware 2.0.2 and used [http://radu.cotescu.com/2009/10/30/how-to-install-vmware-server-2-0-x-on-ubuntu-9-10-karmic-koala/](http://radu.cotescu.com/2009/10/30/how-to-install-vmware-server-2-0-x-on-ubuntu-9-10-karmic-koala/) and it worked fine, then got the plugin for firefox or so, installed windows xp pro and the vmware tools for visual and mouse...

now i need access to my Host harddisks! i need to copy files in and out.
am connected to the internet, on the windows guest, so i think my network is relatively working, but got no idea how to use networking to access my whole harddisk or a certain partition.

i found a way if using a windows host to add a harddisk from ur existing partitions, but cant find how to do it from ubuntu host. 

in vmware infrastructure web interface i tried adding hardware- hdd- it gives me two option, use existing or add new. in both it is refering to virtual disks .vmdk and i have no other option!

ive been researching for two days and trying but alas... 
help would be appreciated! :guitar:

---

### Post by fjgaude on 2010-01-06
One way is to declare shares in Ubuntu, and then through the network in VMware Server access the shares. You will have to establish permissions in Ubuntu so that the LAN users can access the shares. The command line to do this is:

```
sudo smbpasswd -a <id-name-used-in vmware>
```

Other ways are to use the Share functin in Player or Workstation. There you have the drive declared as a Share or any of the drive's partitions or folders.

Have fun!

---

### Post by mach7out on 2010-01-06
i tried that!
didnt really work, i was able to see the ubuntu host in my network places in xp but not enough permissions to access it. 

is there a possibility of a conflict?
my username on ubuntu is the same as my username in vmware, which is also different than my user name in xp.


as for your second suggestion, seems my free vmware has no hdd sharing, and only allows adding new virtual hdd which is pointless to my needs


when i grow older "in ubuntu years" i wanna be just like u
cheers and appreciated

---

### Post by fjgaude on 2010-01-06
Did you give Samba a password like we suggested?

---

### Post by mach7out on 2010-01-11
sudo smbpasswd -a fr33dom
asked for pass
entered pass

---

### Post by fjgaude on 2010-01-11
Okay, maybe you need to setup Shares through this command:

```
shares-admin
```

From there let the files be downloaded, answer the questions, and then declare the share partitions you wish.

This may be done, maybe, through Natilius file-browser: left-clcik on a folder, and then on Sharing Options. Follow the prompts.

Let us know how you are doing.

---

