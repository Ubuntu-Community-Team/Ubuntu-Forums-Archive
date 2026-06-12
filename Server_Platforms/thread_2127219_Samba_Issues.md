---
title: "Samba Issues"
date: 2013-03-19
forum: Server Platforms
---

### Post by chrisbarnes1992 on 2013-03-19
Hello all. I have seem to have some Samba Issues. :-(

I have a Ubuntu server running Samba and NFS for a few months now. NFS has been working perfectly through out but Samba doesnt want to play. I had been using Samba 3.6.3 as from install (Select the tasks), after time the server got slower and slower to a point it took 45 mins to get a 10mb file from the server to a win7 Machine. My Linux Laptop was downloading the same file in under 30 seconds. :icon_frown:

In my eyes that has ruled out any hardware issues and the problem was pointing towards Samba. I had a look around on the servers config files etc i found no change and backed them up. After testing more and more i thought about updating to a later version of Samba. So i used 

```
sudo apt-get purge samba -y
```  

to remove samba. then i used 

```
sudo apt-get update && sudo apt-get samba4 -y
```

I then placed my 3 shares in the config file restarted samba and tried accessing the shares in a XP vm. When I typed in the IP address in the address bar the login box showed up so much faster than the older version of samba ever did. Impressed with the speed of it i then typed my login credentials, Didnt login. So then i went on to the server and re set the smbpasswd for that user. tried to login again, no joy. 4 & a half hours of checking conf files, checking passwords, doing Google searches, drinking coffee etc etc and still no joy. 

Now i have come to the stage where i am completely stumped. :) .

Has anyone got any suggestions?

---

### Post by chrisbarnes1992 on 2013-03-22
I have also tried using a fresh smbd.conf file and a test share and i still have no luck. I have also reset the smbpasswd again just to be sure and still no luck. The client is a XP VM for testing and troubleshooting while i am trying to solve the issue.

---

### Post by matt_symes on 2013-03-22
Thread moved to **Server Platforms**.

You may get a better answer here.

---

### Post by chrisbarnes1992 on 2013-03-23
Thanks for moving my post. Next time ill keep this section in mind when i next need help with my server.

I do also have a quick question which may hopefully get me a bit closer to sorting this issue out. 

Is there any other configuration files i may need to take a look at? This is my first time using samba 4 so i am not in the know of anything new. From my previous experience I only needed to edit smb.conf to make the shares.

---

### Post by chrisbarnes1992 on 2013-03-25
I am still stuck.

Been googleing and trying to get samba working again. Yet again i have found my self making a new smb.conf file from a backup of a original config file. Still will not accept any user names / passwords at all. Has anyone else ran into this issue?

---

### Post by darkod on 2013-03-25
Have you tried setting security = share and use shares without password, just to see if it will work? You can try setting the security later.

---

### Post by Bathroth on 2013-03-25
What kind of error message you get? From the error message we could see where the error can come from ...

Have you given the folders the rights on the groups?
chgrp chown chmod 

for easy testing try chmod 777 /folder/of/samba/share

browesable = yes
guest ok = yes

Regards,
Bathroth

---

### Post by chrisbarnes1992 on 2013-03-25
I have just tried the guest ok = yes and it is asking me for a user name and password to get to the share. Typed in the correct info anyway and still cant get to the share. I amStill testing with a XP VM. I changed the permissions etc on the share to 777 and still Win Xp keeps asking for a user name and password to get access to the share. Again inputting the correct details for about 10 times then gave up.

[COLOR=#000000]browesable = yes[/COLOR] was already added to the share in the config file.

I also added security = share and it has made no difference at all. 

The only way i get a error message to appear is if i type \\192.168.1.10\test in the address bar it pops up saying 

Windows can not find \\192.168.1.10\test. Check the spelling and try again, or try searching for the item by clicking the Start button and then clicking Search.

If i try and map a network drive it keeps asking for a user name and password.

---

### Post by darkod on 2013-03-25
Hmm, with security = share there is no way to ask you for authentication. I have it running at home and access without any problems (and usernames) from win7 desktop and netbook. I'm attaching my smb.conf. The only thing I'm not sure if it plays a role is the workgroup parameter and whether the windows machine has to match it (in windows it's WORKGROUP by default anyway).

---

### Post by chrisbarnes1992 on 2013-03-25
Here is my smb.conf. (Attached) The only thing i have done it is remove the comments, commented out my normal shares and put a test one in. 

Can you use the hosts allowed on certain shares?

---

### Post by darkod on 2013-03-25
Unfortunately I'm not that good an expert for samba. I would make a copy of the original default file, and then create a new empty file putting only the options you need. It will be much smaller and easier to look at.

You can try making it open shares first and then start closing them down. In any case, that default file has loads of options, many commented out, making it even difficult to note what is active and what not.

---

### Post by Bathroth on 2013-03-26
You still have that error?

If yes please tell us about the errorcode or errormessage you get inside of Windows for that we can help you. Because 'an' error can be caused by many stuffs!

Regards

---

### Post by ewangr on 2013-03-26
One other consideration is whether you even need to use Samba. I was having difficulty connecting from Windows to a Samba share on my 12.10 installation. So I removed the share from Samba and tried the Nautilus share option (presuming I would get a better error message), and lo and behold Windows suddenly had no trouble connecting. As with the Samba I would try it first as an "open" share and then apply security.

---

### Post by chrisbarnes1992 on 2013-03-26
Ill try making a blank file see if it start working again. I am guessing you can go ultra basic on the config to only the workgroup its in and the share options. 

I cant really get a error message out of the Xp VM. You keep typing the correct user name and password in but it wont map the network drive nor go to the share. On the main pc's where they have mapped network drives they keep asking for a username and password. Again put it correct details in and still cant get to the server. No matter how many time you type in the user name or password it does nothing. 

As about 1/2 of the Pc's are Windows it would be nice to get access to the network drives again. All of the Linux machines use NFS to get to the server and has been working flawlessly.

The server is a Ubuntu sderver INstall so no GUI etc.

---

### Post by chrisbarnes1992 on 2013-03-27
Wll i have just tried a very basic smb.conf/ Attached screenshot to of how basic. 

Still cant get to the files on the server. Windows keeps asking for a user name and password still. Even though guest is allowed it still wants a user and password. :confused:

No matter how many times is put the correct details in it will not show any messages. This is about 5 mins of typing in the correct username and password non stop. 

Does samba keep any log files somewhere? I have never needed to look into this before with samba. Over the years i have ran many Ubuntu File servers and never came across this issue.

---

### Post by darkod on 2013-03-27
Is the workgroup on the windows machine WORKGROUP?

Are the linux permissions of /mnt/ss set to allow access? The linux filesystem keeps separate permissions from samba. Try after executing this:
```
sudo chmod a+rw /mnt/ss
```

That will give RW to all.

---

### Post by Morbius1 on 2013-03-27
Something to consider:

> Still cant get to the files on the server. Windows keeps asking for a  user name and password still. Even though guest is allowed it still  wants a user and password.
Unlike a Linux Samba client a Windows smb client passes the current user's local login user name and password automatically - even with a guest share. If you have the same user name on the Linux server but have given him a samba password that differs from the Windows local password it will prompt you for credentials.

Either make the passwords match exactly or since you only have a guest share remove the windows user from the samba password database entirely:
```
sudo smbpasswd -x windows-user-name
```

---

### Post by chrisbarnes1992 on 2013-03-27
darkod mentioned and made no differnce. Still not access.

I changed the permissions from darkod's suggestion and no luck.

I also removed the user from database ising the command Morbios1 posted and tried getting onto the test share again. It still pops up wanting a user name and password. I tried the servers local user name and password and nothing apart a box to enter the user name and password.

---

### Post by darkod on 2013-03-27
Did you restart samba after changing the smb.conf? Or restart the server?

There is not much to it, with the latest smb.conf you posted it should work. Or you have another problem somewhere else. Firewall?

---

### Post by chrisbarnes1992 on 2013-03-27
Reset Samba. At the time my laptop was backing up etc so i left it alone. 

However when it was done i re booted the server and is no different.

there is no firewall on the server as well.

---

### Post by chrisbarnes1992 on 2013-03-29
Would NFS effect the samba shares / samba its self. I have got NFS share on the same locations and it has been working fine. I decided to run samba and NFS side by side so i have got good centralized storage for everything.

---

### Post by darkod on 2013-03-29
I don't think so, but I might be wrong. NFS and Samba should be just fine working next to each other, that's the point. You have plenty of servers offering samba for windows machines and nfs for linux/osx machines.

---

### Post by chrisbarnes1992 on 2013-03-29
I have stopped the NFS service using the :

```
sudo /etc/init/d/nfs-kernel-server stop
```

Then re-started samba with :

```
sudo service samba4 restart 
```

Once i done that i got the XP vm going again and i was still un-successful on getting onto the test share. :frown:

Would it be worth trying a Ubuntu Server 12.04 install with NFS and Samba 4 on it and see if it works correctly?

---

### Post by darkod on 2013-03-29
But that's what you have now, right? Ubuntu Server running nfs and samba4?

In any case, if you can make a VM for the server to test if samba shares on it will work fine, it could help at least to see that your thought process is OK. Just be careful about the networking options of the VM, like bridged mode, NAT, etc, because NAT mode can block some things from working as expected.

---

### Post by chrisbarnes1992 on 2013-03-29
I am waiting for all of the updates etc to come through etc. So it is as close as possible to my server setup and get and test from there.

I have the serer on bridged at this moment in time so i can get it setup then i most likely out it on internal network mode so its isolated form my actual network. Wold this be ok? I running the newest version of Virtual-box and I will make snapshots before i go playing etc etc.

---

### Post by darkod on 2013-03-29
I am actually using Bridged on VBox, always, since I want the VMs to be on my LAN. You are not running any services that might interfere anyway, like dhcp server or similar. Letting it be part of your LAN makes it a clear situation networking wise.

Although, since your client XP machine is VM too, using the Internal Network might be OK, both machines will be in same private network.

But making it Bridged makes it possible to check from your host OS too (windows or linux, which ever it is). And also from other machines in your LAN. Not only the XP VM. You will have options to test shares from many more machines, even tablets etc. Imagine if all this time the problem comes from the XP VM. You never checked the share from another machine, because your VBox option is internal network, right?

Just my opinion. I would put both the server and XP VM on Bridged.

---

### Post by chrisbarnes1992 on 2013-03-29
Now a tad concerned, I went on to the server and tried running to update process etc so both the server and the Vm are both totally up to date. Again trying to replicate my server as much as possible.

However when i run 
```
sudo apt-get update
```
it then shows. 
```
sudo unable to open /var/lib/sudo/(user)/0 Read Only File system
```
This is totally out of the blue. Ive never done this before. I have been using sudo etc the whole time i have been trying to suss out what the problemn with samba is.

Whats going on?

---

### Post by darkod on 2013-03-29
Is it possible the root partition was mounted as read-only? Restart the VM and try again.

---

### Post by chrisbarnes1992 on 2013-03-29
Its on my proper server. I wanted them to be updated at the same time so they both have the same packages installed so i can replicate the server as much as possible.

---

### Post by darkod on 2013-03-29
The same applies. Reboot it if you can, and see if it works after that.

You can also ask google how to check if your root is mounted read only. If there was some error that went unnoticed, the root partition might have mounted read only. Or only the mentioned folder is read only.

---

### Post by chrisbarnes1992 on 2013-03-29
Its not re booting :-( . I am half hoping i dont have a hardware issue. And which might of been causing these samba issues.

---

### Post by darkod on 2013-03-29
Were you running the VMs on your physical server? I thought you are doing all that on your desktop, I guess because I do that. :)

I leave my home server alone, I run VBox on my desktop.

When you say not rebooting, you mean it doesn't accept the reboot command because you need sudo for that, or what? I guess you can always force it to shut down on the power button but that should be the last option.

If you google that sudo error, does it give something relevant? You might be able to sort it out without reboot.

---

### Post by chrisbarnes1992 on 2013-03-29
Running VBOX on Desktop for testing.

Server completely locked up. I had to go into my little server area and found it was completely frozen. So i had to hard shutdown. It will not load Ubuntu Server at all on start up.

So i looks like i might have to go into revovery mode for the first time on the physcal server (ever). I will e very annoyed if it was a hard drive failed. 5 of the 8 hard drives are under a year old.

While i was waiting for the server to boot up in recovery mode I tested Samba 4 on Ubuntu Server 12.04LTS with NFS running along side it, It does exactly the same thing. Im guessing there is a issue somewhere which causes Samba to not authenticate to the shares.

---

### Post by chrisbarnes1992 on 2013-04-02
Been doing some more digging and i am guessing there is some sort of issues with some of the latest updates which effect Samba 4. Because when i go back to a fresh install snap shot of Ubuntu 12.04.2 Server Samba 4 work fine but when it updated it stops working. 

My server is still working ok with NFS and still not sure what caused the problem of it going into read only mode. In the end i had to remove Samba 4 and went back to 3.6.3 to get the Windows Box's to connect to the server again. It is still performing very slow but it will do for the mean while.

---

