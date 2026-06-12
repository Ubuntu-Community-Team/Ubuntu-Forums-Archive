---
title: "virt-manager tunnel over ssh not available. Kubuntu 15.04"
date: 2015-06-07
forum: Virtualisation
---

### Post by mccalleyt on 2015-06-07
I have a fresh install of Kubuntu 15.04 x86-64 and I installed virt-manager and tried to setup a new connection and I couldn't use the QEMU/KVM tunnel over ssh option. It was there but grayed out. Please help.

Thanks,
mccalleyt

---

### Post by TheFu on 2015-06-07
Can your account ssh into the KVM host outside virt-manager using a non-root account?
root isn't needed.
Is your account in the libvirtd group on both the client and the VM host?
Have you setup ssh-keys between the systems? I suppose passwords could work, but I've **never** done it that way.

---

### Post by jason_gibson2 on 2015-06-07
If the ssh-askpass package isn't installed then you won't be able to connect virt-manager over ssh. Install package ```
sudo apt-get install ksshaskpass
```

---

### Post by mccalleyt on 2015-06-07
>  		 		 		 		[h=2]Re: virt-manager tunnel over ssh not available. Kubuntu 15.04[/h] 		 				 				 		 			 				[INDENT] 					Can your account ssh into the KVM host outside virt-manager using a non-root account?
root isn't needed.
Is your account in the libvirtd group on both the client and the VM host?
Have you setup ssh-keys between the systems? I suppose passwords could work, but I've **never** done it that way. 				[/INDENT] 			
  			   		
 			 				 			 			 			 		
 	


I tried running it as root, but it didn't work. It still was grayed out.

---

### Post by mccalleyt on 2015-06-07
> If the ssh-askpass package isn't installed then you won't be able to connect virt-manager over ssh. Install package    
     ```
sudo apt-get install ksshaskpass
```


That is already installed.

---

### Post by TheFu on 2015-06-07
> **jason_gibson2 said:**
> If the ssh-askpass package isn't installed then you won't be able to connect virt-manager over ssh. Install package ```
sudo apt-get install ksshaskpass
```

Excellent!  That could be it, provided the libvirtd group membership is correct.
**ssh-askpass** - is all I have installed on 1 machine where this works.

However, I do not have it on another system. Both work fine with virt-manager - probably because I use ssh-keys.

I will re-iterate. Do NOT run or connect as root.

---

### Post by mccalleyt on 2015-06-07
> Excellent!  That could be it, provided the libvirtd group membership is correct.
**ssh-askpass** - is all I have installed on 1 machine where this works.

However, I do not have it on another system. Both work fine with virt-manager - probably because I use ssh-keys.

I will re-iterate. Do NOT run or connect as root.


That program is also installed as well. I can say that Filezilla is having issues as well, I use pubkeys as well. I don't get the GUI screen asking for the key pass-phrase like I used to in Kubuntu 14.04, I am currently running Kubuntu 15.04 with any program that uses SSH to connect to a remote host. Filezilla doesn't ask for the password to my keys and will not connect to my remote systems.

---

### Post by mccalleyt on 2015-06-07
I found a temporary fix for the filezilla issue. I had to create a script to add the key password to the kwallet (of which only stays until I logout), but I have to run this script every time I login. It used to ask for the key password once when I first tried to access the remote systems using filezilla or the cli ssh application then it wouldn't ask for it again until I logged out and then back in again. Virt-manager still doesn't have the remote connection option available. ```
 #!/bin/sh
# set SSH_ASKPASS if not set elsewhere
export SSH_ASKPASS=/usr/bin/ssh-askpass
ssh-add </dev/null
```

---

### Post by TheFu on 2015-06-07
> **mccalleyt said:**
> I found a temporary fix for the filezilla issue. I had to create a script to add the key password to the kwallet (of which only stays until I logout), but I have to run this script every time I login. It used to ask for the key password once when I first tried to access the remote systems using filezilla or the cli ssh application then it wouldn't ask for it again until I logged out and then back in again. Virt-manager still doesn't have the remote connection option available.

What does filezilla have to do with virt-manager?  Sounds like a different issue to me. 1 issue at a time is best.

I provided specific things to check. Did you check those things? 

I setup libvirt/kvm all the time. Those are the necessary things for a 14.04 server from a 14.04 client.
It isn't clear if you've configured the ssh-keys properly. Directory and file permissions on ~/.ssh/ matter on both the server AND the client.
Is ssh-agent setup and running?

Does **ssh userid@server** work as expected? Any warnings or errors? Best to start from the beginning at this point.

---

### Post by mccalleyt on 2015-06-07
> What does filezilla have to do with virt-manager?  Sounds like a different issue to me. 1 issue at a time is best.

I provided specific things to check. Did you check those things? 

I setup libvirt/kvm all the time. Those are the necessary things for a 14.04 server from a 14.04 client.
It isn't clear if you've configured the ssh-keys properly. Directory and  file permissions on ~/.ssh/ matter on both the server AND the client.
Is ssh-agent setup and running?

Does **ssh userid@server** work as expected? Any warnings or errors?

Sorry I was only providing that issue in case they have any relation to each other. I did try the stuff you said to do with no avail. I made sure the permissions we set to 600. ssh userid@server does work as it should, ssh-agent is working.

---

### Post by TheFu on 2015-06-07
Please post the output from the commands you use to prove things. 
**ls -la ~/.ssh/**
 and 
**id** 
on both systems.
```
thefu@c720:~/.ssh$ ls -al
total 60
drwx------  2 thefu thefu  4096 Jun  7 06:44 ./
drwxr-xr-x 90 thefu thefu  4096 Jun  7 11:58 ../
-rw-------  1 thefu thefu   783 Feb 19 07:18 authorized_keys
-rw-------  1 thefu thefu  1888 Jun  1 08:02 config
-rw-------  1 thefu thefu  1675 Nov 15  2014 id_rsa
-rw-r--r--  1 thefu thefu   389 Nov 15  2014 id_rsa.pub
-rw-------  1 thefu thefu 17832 Jun  7 06:44 known_hosts
-rw-------  1 thefu thefu 12852 Aug 10  2014 known_hosts.old

thefu@c720:~/.ssh$ id
uid=1000(thefu) gid=1000(thefu) groups=1000(thefu),4(adm),24(cdrom),27(sudo),30(dip),46(plugdev),110(lpadmin),111(sambashare),120(libvirtd)

```

We will figure this out. I have to step out for the rest of the afternoon in an hr or so, but will see any posts.

---

### Post by mccalleyt on 2015-06-07
**ls -la ~/.ssh/**
```

 [FONT=monospace][COLOR=#000000]total 24 [/COLOR]
drwxrwxr-x  2 mccalleyt mccalleyt 4096 Jun  7 11:18 [COLOR=#5454ff]**.**[/COLOR]
drwxr-xr-x 60 mccalleyt mccalleyt 4096 Jun  7 11:26 [COLOR=#5454ff]**..**[/COLOR]
-r--------  1 mccalleyt mccalleyt  133 Jun  7 11:18 agent-rock-top 
-rw-------  1 mccalleyt mccalleyt 1766 Feb 24 14:33 id_rsa 
-rw-------  1 mccalleyt mccalleyt  400 Feb 24 14:33 id_rsa.pub 
-rw-rw-r--  1 mccalleyt mccalleyt  790 Jun  7 11:03 known_hosts
[/FONT]
```[FONT=monospace]

id
[/FONT]```
[COLOR=#000000]uid=1000(mccalleyt) gid=1000(mccalleyt) groups=1000(mccalleyt),4(adm),5(tty),20(dialout)[/COLOR]
[FONT=monospace],24(cdrom),27(sudo),30(dip),46(plugdev),115(lpadmin),120(ssh),130(sambashare),131(vboxus
ers),133(libvirtd),134(kvm)
[/FONT]


```

The server side works with my other machines. The server is configured properly.

---

### Post by TheFu on 2015-06-07
The directory and file permissions are WRONG for ssh to work. Please make them like mine.
On the server, what are the groups as show by **id**?


Whoa - -  do you have both KVM and virtualbox installed on the same machine?  Or is this the client we're seeing?  That should be ok, but on the KVM server, only 1 hypervisor should be installed.

---

### Post by mccalleyt on 2015-06-07
I changed the file properties on the ~/.ssh files to what you displayed. Virtual Box is only on the client side.

The Server side.....

ls -la ~/.ssh/
```

 [FONT=monospace][COLOR=#000000]total 12 [/COLOR]
drwxrwxr-x  2 mccalleyt mccalleyt 4096 May 20 13:27 [COLOR=#5454ff]**.**[/COLOR]
drwxr-xr-x 12 mccalleyt mccalleyt 4096 Jun  7 01:06 [COLOR=#5454ff]**..**[/COLOR]
-rw-------  1 mccalleyt mccalleyt 1263 May 20 13:27 authorized_keys
[/FONT]
```[FONT=monospace]

id
[/FONT]```
 [FONT=monospace][COLOR=#000000]uid=1000(mccalleyt) gid=1000(mccalleyt) groups=1000(mccalleyt),4(adm),24(cdrom),27(sudo)[/COLOR]
,30(dip),46(plugdev),111(libvirtd),112(lpadmin),113(sambashare)
[/FONT]
```[FONT=monospace]
[/FONT]

---

### Post by mccalleyt on 2015-06-07
Having said all that. I can connect to the server from my other machine using virt-manager just fine. When I try to add the connection to virt-manager on this machine the "Connect to remote host" section is grayed out. I cannot add a connection to the remote server in virt-manager.

---

### Post by mccalleyt on 2015-06-07
[IMG]http://i54.photobucket.com/albums/g119/mccalleyt/virt-managerissue2.png[/IMG]

---

### Post by TheFu on 2015-06-07
Fix the ~/.ssh/ directory permissions on the server-side. 600 is fine for most files inside. Directory **MUST** be 700, period.  Anything else shouldn't work.

Test that ssh works after.  I'm surprised ssh worked before - to the point that I'm having a hard time believing it. Correct directory and file permissions are core to ssh working. For pushing keys from a client to a server, use **ssh-copy-id** - that method won't screw up the directory or file permissions.
[ATTACH=CONFIG]262476[/ATTACH]

See the checkbox?  Your screen isn't showing that for some reason.

The group stuff looks file on both the server and client. I'm left thinking it is the directory permissions on the server stopping this.

I bet filezilla with sftp will work now.

---

### Post by mccalleyt on 2015-06-07
I have had filezilla working and ssh has been working from the start before I  first posted the my question. I got it working with the script I setup. For some reason filezilla wont invoke the system to have the key opened and ask for the key password. It works if I execute the script ```
#!/bin/sh 
# set SSH_ASKPASS if not set elsewhere 
export SSH_ASKPASS=/usr/bin/ssh-askpass 
ssh-add </dev/null
```  I have only found a temporary "bandaid" for my pubilc key access issue.

---

### Post by TheFu on 2015-06-07
I've never used filezilla. From windows, winscp is my poison. From UNIX/Linux, the CLI or any file manager with sftp:// works.  I've neve setup anything related to ASK-PASS either - not once.

Be back in 5-ish hrs.

---

### Post by mccalleyt on 2015-06-07
k thanks. I am usually always in front of my computer during the day.

---

### Post by mccalleyt on 2015-06-16
Ok after some time away from my computer I found the problem is PEBKAC.  The checkbox that is normally shown for connection to remote host blends  in with the window. It appears just in the photo I posted earlier that  the box isn't there at all. When I clicked a few times around the area  where the check box should be then it appeared as a checkmark without a  box. This might pose a small problem with other applications as well.  How do I submit a bug or otherwise report to fix this problem? I have  ran into the same thing with a few other applications as well.

---

### Post by TheFu on 2015-06-16
So post #17 wasn't the answer?

---

### Post by mccalleyt on 2015-06-16
Nope all my keys were working properly but the options were grayed out  and the check box isn't there. You can't see the box at all. It is all  gray just like the window. Can you see the picture I posted on post #16? It shows the window that I can see, it is a screenshot of the actual window i see.

---

### Post by TheFu on 2015-06-16
> **mccalleyt said:**
> Nope all my keys were working properly but the options were grayed out  and the check box isn't there. You can't see the box at all. It is all  gray just like the window. Can you see the picture I posted on post #16? It shows the window that I can see, it is a screenshot of the actual window i see.

You post an image with a **washed out screen** which doesn't show the expected checkbox.
I post an image with a **clear screen** - which does show the checkbox and suggest it needs to be checked.
Clicking around in the place where the checkbox is (but isn't seen) and it gets checked AND the connections start working.

Perhaps the long-term workaround is to pick a different theme, but checking the invisible checkbox will still be required.

BTW, all the permissions stuff for ~/.ssh/ is important to ssh connections too.  I learned it the hard way years ago. Researched **exactly** the required permissions.

Regardless - glad you found the checkbox, clicked it and that it is working now. Looking at the "autoconnect" checkbox (which I never check), it doesn't have much/any outline either.  Still - if you change to a different theme, I bet these things will be easier to see.

Or did I completely miss what the fix was?

---

