---
title: "sharing files with virtualbox ubuntu hardy and xp"
date: 2008-05-27
forum: Virtualisation
---

### Post by alonips on 2008-05-27
i have installed xp as guest in a ubuntu hardy host.I have installed samba but i can't still see in windows any of the folders that i have shared can anyone please tell me how to make this work i want to have folders from linux available to use with some xp programs. help me with these please :)

---

### Post by k@e on 2008-05-27
You don't need Samba to share files between Windows XP guest and Ubuntu host. Make sure you have installed the vbox guest additions in your guest operating system (XP). In the VirtualBox main screen open the config dialog for the guest machine. There you can add a folder of the host os that the guest can access, too. If not done automatically, you just have to map a virtual drive in Windows Explorer.

---

### Post by alonips on 2008-05-27
i have installed guest additions on the guest in this case xp but the file that i have choose to share in virtual box does not appear in the xp network places on shared folders

---

### Post by starcannon on 2008-05-27
Have you tried running the *Add a network place* wizard? Thats how I got my shared folder to show up under *My Network Places*.

I've installed Virtual Box with WinXP on 2 different machines in the last 2 days, yesterday was my first time ever, it took me a bit to get the hang of it, today it went really smoothly. I'm no guru at it yet, but I have managed to get it up and going with a shared folder on 2 machines, I'll help you where I can.

---

### Post by alonips on 2008-05-27
can it be because i have installed VirtualBox OSE and not the full VirtualBox package?

---

### Post by starcannon on 2008-05-27
Not sure, I've been using the full package, its free (as in beer) to use, and has all the features, so I just went with that /shrug.

---

### Post by alonips on 2008-05-27
ok i have installed the full version but the folder doesn't appear i have chosen to add network place but asks for the internet or network address what do i put here my folder path is /home/bernardo/Music. help me please

---

### Post by alonips on 2008-05-27
Can anyone tell me step by step how have manage to share folders from ubuntu has host and xp as guest to work.
 There are two types of shares:??I need to configure in the terminal in ubuntu and in run in xp??
i have virtualboz installed and working with guest additions installed but i really need to access files that belong to the host, one thing is that the partitions are in ntfs format i don't know if this is a problem? Please any help...

---

### Post by alonips on 2008-05-28
i think this is the problem.
VBoxManage sharedfolder     add <vmname>|<uuid>
                            -name <name> -hostpath <hostpath>
                            [-transient] [-readonly]


Syntax error: Not enough parameters
bernardo@bernardo-desktop:~$                    -hostpath "/home/bernardo/Music"

Can someone explain me what do i need to do for this to work the path for the folder is /home/bernardo/Music , why does it saynot enough parameters.

---

### Post by starcannon on 2008-05-28
I just used the Network Places wizard gui to browse to the folder, I didn't have to type anything.

---

### Post by alonips on 2008-06-01
ok thanks i've done it it was the path that was not typed right.
I will post a final reply explaining my problem and the step by step to make shared folders work.tank you

---

### Post by dcharry on 2008-07-05
The easiest way to share is to use VirtualBox build in function, in your xp setting there's a shared folder section, add the location from your ubuntu folder so that you could see it in your windows xp, it works perfectly well on my machine, although I only use VirtualBox OSE.

---

### Post by ckomurlu on 2008-09-25
Hi, I have a hardy heron host and WinXP SP2 guest with VirtualBox OSE 2.0_2.0.2. I could install guest additions. I can reach internet in both environment. But guest does not have a valid IP address in the subnetwork to which both environments are included. It's assigned 10.0.2... while, Router assigns always IP's as 10.1.1...
I have checked DHCP clients in router's list, I see the host computer as expected, but the guest OS is not in the list.
Guest and host cannot ping each other. Host can ping a remote machine in the subnetwork. Guest can ping nobody.
First I tried to share a local folder (say `folderAtGuest´) created at guest and reach to that folder from host, via browsing  all the subnetwork in smb protocole using nautilus. Host can see the guest computer in windows workgroup list but cannot see the folder (folderAtGuest). In addition, a remote machine, by the same way, can see the guest machine in network places list, but cannot access the shared folders.
Reversely, I tried, just as described in this thread, to create a folder (say `folderAtHost´) in host and add this folder using VirtualBox main settings, then browse in guest, my network places. I could see the folder, added in my network places. Well, the folder (`folderAtHost´) is added to my network places, but when I browse that folder I'm led to `All Users\Documents´ folder which is created in local file system of guest.

Another point is that, I can reach a shared folder created in a remote windows machine and transfer files by both, host and guest.

Might I have made a mistake in VirtualBox settings interface? Creating a folder in host and trying to access it from guest?

Thanks in advance.
Sorry, if this is already discussed in other threads.

---

### Post by xboxfox on 2008-10-07
hi guys 
if you want to get shared folders when machine is running click devices and then click shared folders tell it wat folder u want thengo into network places and up the top in the address bar write entire network and then it will bring you to a new place and a folder called virtual box shared folders and then your ubuntu stuff will be there.
hope this helps 
xboxfox

---

### Post by jrsc109 on 2008-10-07
This seems like it should be the easiest thing to do, but I am having real difficulty achieving it.

I have shared the relevant folders in Ubuntu (8.04) and I have created the share using the Devices menu on VirtualBox in the guest (WinXP)

I have installed VirtualBox Guest Additions

However, when I go to the shared folders, or try to add a network place, in the guest, there is nothing there.

What am I missing?

---

### Post by xboxfox on 2008-10-07
1.when machine is running go to devices-shared folders and make a shared folder
2.go into my networkplaces then seach for entire network then a folder labled virtual box shared folders will be there and then in the folder the ubuntu folders will be there

hope this helps 
xboxfox

---

### Post by Konsolkongen on 2008-12-29
Are there any risks when sharing a folder in Linux that Windows users can write to? I'm thinking virus and spyware that might throw files over to the Linux folder? Can it do that and should i care? Can the windows virus harm the Linux files when windows is running and can the spyware make the computer slower?

---

### Post by akelsall on 2009-01-01
I had this same issue (with Intrepid this time) and got it going by doing the following:

1. Run Virtualbox and log into your guest (mine is XP).

2. Open Explorer

3. Click Tools | Map Network Drive

4. Click Browse and browse to the Linux folder you defined as your shared folder. 

After doing this, initially I didn't see it, I rebooted the Guest OS (XP) and now I see it and can access files in the shared folder. Don't know why simply defining the shared folder wasn't enough (it was in Hardy for me). 

HTH,

Andy

---

### Post by nirvblakr on 2009-01-19
When you open My Network Places, just click the folders icon at the task bar.  Click Entire Network and you will see Microsoft Windows Network and Virtual Box Shared Folders.  When you click the latter, you will see your shared folder. 

Hope this helps.

---

### Post by Fire_Wolf on 2009-02-05
I had the same problem...now solved! I use Ubuntu 8.10 version has host and Windows XP as guest. 

After installing guest additions I opened the ms-dos window and typed: 

net use x: \\vboxsvr\<wright your shared folder name here>

Now open My computer, and you should see your shared folder.


Hope this helps!

---

### Post by vijaybilgoji on 2009-08-05
**_How to share folder's between Ubuntu 8.04 & Xp in virtual machine._**

**1**.Use the Virtual box 3.0.4 non free version for sharing folder in virtual machine.You can get it here
[http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)

**2**.Download the virtual box guest additions .iso file from this site
[http://download.virtualbox.org/virtualbox/3.0.4/VBoxGuestAdditions_3.0.4.iso](http://download.virtualbox.org/virtualbox/3.0.4/VBoxGuestAdditions_3.0.4.iso)

To install guest additions-

Start xp machine-go to Device---Mount CD/DVD ROM---CD/DVD ROM Image---ADD---Select.

Complete the setup and Poweroff Virtual Machine.

**3**.Open Virtual Box-
In Settings---Shared Folders---Add the Folder you want to share----Click Ok.

**4**.Start XP-
Right Click START---Right Click MY NETWORK PLACES---MAP NETWORK DRIVE----SELECT THE DRIVE NAME OF YOUR CHOICE---
Show the folder you want to share by Browsing it in Virtual box shared folders link.

Click OK & FINISH.

Now You can see the Shared folder in My computer.
Enjoy Ubuntu:)

---

