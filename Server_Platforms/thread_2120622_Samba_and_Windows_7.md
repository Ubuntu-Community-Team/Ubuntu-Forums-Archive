---
title: "Samba and Windows 7"
date: 2013-02-27
forum: Server Platforms
---

### Post by joshbcs on 2013-02-27
Hello everyone, I have been trying to setup samba on my ubuntu 12.04 LTS machine for file sharing with windows 7, so far i am keep getting "access denied" from my windows 7 client.

I have googled everywhere and tried all sorts of things but still getting this "access denied" problem

my steps were:
1) install samba on my ubuntu 12.04 LTS machine
2) i edited the smb.conf: 
    i) to the correct workgroup name
    ii) wins support = yes
    iii) name resolve order = wins lmhosts hosts bcast
3) in the folder i want to share, i have also set up:
    i) correct path
    ii) browsable = yes
    iii) guest ok = no
    iv) writable = yes
    v) valid users = the users for my windows 7 client (for example user1)
    vi) create mask = 0755
4) then i went to ubuntu system and created user1
5) went back to samba and created smbpasswd -a user1, with password
6) i went to the folder i wanted to share, click Sharing Option, allowed to share

7) i went to my windows 7 machine, type in the server ip, \\192.168.x.xxx and found the folder
8) i right click the folder and press MAP.....
9) when i click in, it asked for username and password, i tried:
     i) [email]user1@192.168.x.xxx[/email] and password, didn't work
     ii) user1@server name and password, didnt work
     iii) i went to administrative tool, local security policy and uncheck the 128bit encrypt thing and also the send LM & NTLM response thing, i didn't work

10) last thing i tried is format all the windows 7 machine, and the ubuntu machine and redo all the steps and it didn't work

please help.....desperately need help....thanks

---

### Post by GordThompson on 2013-02-27
Try this: When Windows prompts you for the username, just enter 'user1' and omit the '@...' stuff.

---

### Post by joshbcs on 2013-02-27
> **GordThompson said:**
> Try this: When Windows prompts you for the username, just enter 'user1' and omit the '@...' stuff.

tried, access denied and it stop allowing me type in user and password again unless reboot...

---

### Post by GordThompson on 2013-02-27
What, if anything, does the following Terminal command display?

```
dpkg --get-selections | grep libpam-smbpass
```

---

### Post by GordThompson on 2013-02-27
I just enabled folder sharing on a fresh Ubuntu 12.04 LTS virtual machine and I didn't have to mess with smb.conf at all. I just created the folder...

/home/gord/Shared

...in Nautilus, then I right-clicked on it, chose "Sharing Options", ticked "Share this folder", and let the system install samba and libpam-smbpass. When that was done I restarted the machine and once it was back up and running I was able to access "\\192.168.1.100\Shared" from a Windows machine.

I'm wondering if you are running into the "there are two ways to share a folder" issue summarized here:

[http://ubuntuforums.org/showthread.php?p=10502478#post10502478](http://ubuntuforums.org/showthread.php?p=10502478#post10502478)

---

### Post by volkswagner on 2013-02-27
First  verify user1 has access to samba.  From the server try smbclient to test the user's credentials.

```
smbclient //fileserver/share -U user1
```

This should give you a command prompt where you can perform simple commands like ls to list files.
to exit:
```
quit
```

For more info check man pages.

```
man smbclient
```

Can you access the share without first trying to map the drive.  What happens when you simply try to open the shared folder from Window 7 client?

Did you restart Samba services after making your changes?

Do you get any errors when running testparm?
```
testparm
```

Does your Windows 7 username match the username of a different samba user?  Perhaps windows is sending your session username?  Samba works well if your windows username and password match those on the samba server.

---

### Post by Morbius1 on 2013-02-27
> 3) in the folder i want to share, i have also set up:
    i) correct pathYou also might want to check the Linux permissions on the shared folder to see if these users actually have access to it:
```
ls -al /path/to/shared/folder
```[COLOR=Blue][I]BTW, If you have libpam-smbpass installed be aware of it's consequences. If you set a samba password for a user ( i.e., sudo smbpasswd -a user1 ) it will work fine for that session but reboot the machine and it overrides that samba password  and replaces it with that users local Linux login password.

I can't think of one situation where you would ever want a system to do that in either an enterprise environment or especially in a home network. Removing that package has no other consequences since that is all it does.[/I][/COLOR]

---

### Post by joshbcs on 2013-03-01
Thank you everyone for all the support.
I was away from my country for few meetings and hopefully be back this weekend to try all the aid above.

Thanks again, appreciate so much.

---

