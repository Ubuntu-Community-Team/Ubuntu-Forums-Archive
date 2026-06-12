---
title: "New to servers - &quot;No such file or directory&quot;?"
date: 2011-08-04
forum: Server Platforms
---

### Post by Arachan on 2011-08-04
Hello,

I have recently built a server which I hope will be a long-ish term project to set up with a mail server and backups and lots of things. At the moment however all I'm running on it is a minecraft server; I also want to set up a Call of Duty 4 server. I have it running at the moment on my desktop, and I want to move it to the server. 

Now, my problem: I have copied all the COD4 files over to a directory on the server. I try to run the server with the command:

```
sh /media/DATA/COD4SERVER/cod4_lnxded
```but I get the error:

```
-bash: /media/DATA/COD4SERVER/cod4_lnxded: No such file or directory
```however the output of 

```
ls /media/DATA/COD4SERVER
```includes cod4_lnxded.

I don't think it's a permissions error, I gave the file full permissions just to test it.

Any ideas of what could be the problem?

Thanks,
arachan.

---

### Post by WhiteHorse on 2011-08-04
try ksh instead of sh

---

### Post by hakermania on 2011-08-04
> **WhiteHorse said:**
> try ksh instead of sh
-1

The filename could include even newlines that you don't even know that exist!
Would it be a problem if you rename the server?
Also, could you paste the actual output of ls inside [code] tags?

---

### Post by Wim Sturkenboom on 2011-08-04
Did you use tab completion? You might have confused an lowercase 'l' and an uppercase 'I' or so?

---

### Post by Joseph889 on 2011-08-04
Is the server 32 bit or 64 bit? Try downloading the 32 bit libraries if its 64 bit. ```
sudo apt-get install ia32-libs
```

---

### Post by Arachan on 2011-08-04
Thanks for the replies.

I tried ksh - got the standard 'package not installed' message. As ksh was also advised against I have not installed it. 

I do use tab completetion, so I am sure I am inputing it correctly. The output of 

```
cd /media/DATA/COD4SERVER
ls
```

is: 

```
1SETUP       cod4_lnxded      codlogo.bmp  libgcc_s.so.1     main   mss32.dll     zone
binkw32.dll  cod4_lnxded-bin  iw3mp.exe    libstdc++.so.6    miles  pbsetup.run
cod4.ico     cod.bmp          iw3sp.exe    localization.txt  Mods   README.linux
```I am unsure if renaming it would work, although I think not. However, I tried nonetheless, and I get the same error. I also tried, just as a test:

```
nano ./cod4_lnxded
```and it opened and I got the expected bunch of goobledegook (what is the actual name?)

Any other ideas?

Thanks,
arachan.

---

### Post by Gyokuro on 2011-08-04
should be: ./media/DATA/COD4SERVER/cod4_lnxded

---

### Post by Arachan on 2011-08-04
Are you sure? I thought that "." referred to the current directory - therefore it is just a shortcut, eg /media/DATA is the same as ./DATA but ONLY IF you have used cd /media already. 

Someone prove or disprove me?

Thanks.
arachan.

---

### Post by Wim Sturkenboom on 2011-08-04
> **Arachan said:**
> Are you sure? I thought that "." referred to the current directory - therefore it is just a shortcut, eg /media/DATA is the same as ./DATA but ONLY IF you have used cd /media already. 

Someone prove or disprove me?

Thanks.
arachan.As far as I know you're right.

---

### Post by fdrake on 2011-08-04
can you post the output of
```
ls -al /media/DATA/COD4SERVER/cod4_lnxded
```
i know you said you gave to it full access but you never know... :P

---

### Post by Arachan on 2011-08-05
Hello.

The output of:

```
ls -al /media/DATA/COD4SERVER/cod4_lnxded
```

is the expected:

```
-rwxrwxrwx 1 arachan arachan 2278332 2011-08-03 21:27 /media/DATA/COD4SERVER/cod4_lnxded
```

The command I ran to give it full permissions is:

```
sudo chmod 777 /media/DATA/COD4SERVER/cod4_lnxded
```

Hmmm... I really have no idea what the problem could be.

I hope someone more knowledgeable than I will see something I've missed.

Thanks for the help,
arachan.

---

### Post by Wim Sturkenboom on 2011-08-05
You're problem might be with /media and/or/media/DATA (the mounting)

Copy the stuff to your home directory and try again.

---

### Post by Arachan on 2011-08-05
Hello.

Well, that sounded like a good idea, so I tried it. I got the same error though.

I am really lost as to what could cause this.

Thanks,
arachan.

---

### Post by volkswagner on 2011-08-05
Have you tried using sudo?  I know the file is owned by you, but it's worth a shot.

```
sudo sh /media/DATA/COD4SERVER/cod4_lnxded
```

---

### Post by Arachan on 2011-08-05
Hello.

I tried your suggestion. I get a new error this time, which seems to be related to the contents of the file itself:

```
/home/arachan/COD4SERVER/cod4_lnxded: 1: Syntax error: ")" unexpected
```

If this is indeed related to the contents of the file, then at least it's acknowledging it's existence... 

Thanks,
arachan.

---

### Post by Arachan on 2011-08-07
Hello.

Anyone got any other ideas?

Thanks,
arachan.

---

### Post by Arachan on 2011-08-17
bump

---

### Post by fdrake on 2011-08-17
this is kinda of ambiguous ....

are you running bash (sh) with your user in your local machine or from a remote machine?

also i would check if another program is accessing that file
```

sudo lsof /media/DATA/COD4SERVER | grep cod4_lnxded

```

---

### Post by jramshu on 2011-08-17
What about the file owner permissions? 

The server won't be able to access them if they are different.

Just a thought.

---

### Post by Arachan on 2011-08-17
Hello,

I am logging in to the server using PuTTY from my desktop computer (the server is on my desk next to me though, and I have tried logging in locally too).

I tried 

```
sudo lsof /media/DATA/COD4SERVER | grep cod4_lnxded
```

but got no output. 

I'm not 100% sure how to change file owner permissions, is it

```
sudo chown arachan:arachan /media/DATA/COD4SERVER/cod4_lnxded
```

Thanks,
arachan.

---

### Post by fdrake on 2011-08-17
ok from what i understood your are logging in into your server right? and the file of the server are mounted on your desktop (arachan desktop?) to the  /media/DATA folder right?  well in your server pc (not the arachan desktop!) what is the path of your data? (is it on the dekstop or home?) 

it looks to me that you are trying to run a program logging into your server and putting the mounting path of the data that belongs to the pc desktop (that's why the server cannot find the file becouse it's not on its path, i guess....)

---

### Post by jramshu on 2011-08-17
I've never set up a game server but on my regular old lamp server the files are placed in /var/www. 


Yes, chown is how you change ownership. 

EDIT: Nevermind, researching the cod4 server installation guides.

---

### Post by Arachan on 2011-08-17
Hello,

Sorry fdrake, I think you misunderstand. I am logging into my server with PuTTY, which as far as I know pretty much acts as if I am logging in locally. The path that I have been referring to thus far (/media/DATA/COD4SERVER) is a local path on my server computer (aServer) not my desktop computer (arachan-desktop). So I have been connecting to aServer from arachan-desktop but have been doing everything on aserver, not arachan-desktop. 

I hope this clarifies things.

It's weird, I can run the cod4 server fine on arachan-desktop, but when I copy all the files for it over to aServer and run the same command to start it as usual, it doesn't work.

Please note this is my first time using a CLI only system, and I am not well-versed in the ways of the CLI, but I am learning :)

Thanks,
arachan.

---

### Post by jramshu on 2011-08-17
What's the user name on aServer? Is the same as the file owner name?

EDIT: Have you tried cd-ing to the folder and starting it from there? Have you tried running it from the server itself, or just through putty?

---

### Post by Arachan on 2011-08-17
Hello,

On aServer the user that I am logging in as is arachan, same as on arachan-desktop. 

I tried 

```
cd /media/DATA/COD4SERVER/
./cod4_lnxded
```

but got the same error as usual. 

I'll try hooking up a monitor and keyboard to aServer and trying locally.

Thanks,
arachan.

---

### Post by jramshu on 2011-08-17
Everything I find on a cod4 server is one of three things;
1. File ownership permissions
2. Path to file
3. 64 and 32 bit architecture

---

### Post by fdrake on 2011-08-17
i don't use PuTTY but it is similar to ssh, try if this works;
```

ssh arachan@IPADDRESS
(enter password)
sh /media/DATA/COD4SERVER/cod4_lnxded

```

where IPADDRESS is the ipadress of the aserver on your local net.

---

### Post by Arachan on 2011-08-17
Hello,

I tried locally, no luck, same error. Okay, so the permissions of the file in question are:

```
-rwxrwxrwx 1 arachan arachan 2278332 2011-08-06 06:24 cod4_lnxded
```

I don't know much about permissions, but this seems to state that arachan is the owner, from group arachan, and everyone has read, write and execute permissions. I know this is pretty lax security, I just set the permissions of this file like this to test if permissions were the cause of my problems. 

I'm fairly sure the path is correct, it shows up with an ls (as shown above).

Both arachan-desktop and aServer are 64-bit, and both are running Ubuntu 11.04 (albeit one is running the desktop version and the other the server version, of course).

Thanks,
arachan.

---

### Post by Arachan on 2011-08-17
> **fdrake said:**
> i don't use PuTTY but it is similar to ssh, try if this works;
```

ssh arachan@IPADDRESS
(enter password)
sh /media/DATA/COD4SERVER/cod4_lnxded

```where IPADDRESS is the ipadress of the aserver on your local net.


Hello,

Hmm... this seems very similar to PuTTY, tbh I am only using PuTTY because it was recommended to me, I suppose I could use plain ssh instead. 

Anyway, I tried your suggestion, and got the same error as I get from PuTTY and also a local login

```
-bash: /media/DATA/COD4SERVER/cod4_lnxded: No such file or directory
```

Thanks,
arachan.

---

### Post by fdrake on 2011-08-17
2 questions:

1-is the DATA folder just a folder in the media folder or is the mountpoint of a device  (like usb drive) 
    If so can you post (while your are logged in with ssh)
    ```

     less fstab
    
```

2-did you try to do this locally with the server? what's the result?

---

### Post by Arachan on 2011-08-17
> **fdrake said:**
> 2 questions:

1-is the DATA folder just a folder in the media folder or is the mountpoint of a device  (like usb drive) 
    If so can you post (while your are logged in with ssh)
    ```

     less fstab
    
```2-did you try to do this locally with the server? what's the result?

Hello,

/media/DATA is the mount point of sda5. The respective line in /etc/fstab is:

```
/dev/sda5               /media/DATA     ext4    defaults                       0        2
```

As I said before, I did try locally, and got the same error.

Thanks,
arachan.

---

### Post by fdrake on 2011-08-17
ok i think we have a path of the problem : 64-bit.

the permissions and the commands are fine. 

```

sudo apt-get install lsb-core-ia32 lsb-core

```

reboot the server and try

---

### Post by Arachan on 2011-08-17
> **fdrake said:**
> ok i think we have a path of the problem : 64-bit.

the permissions and the commands are fine. 

```

sudo apt-get install lsb-core-ia32 lsb-core

```reboot the server and try

Hello,

I ran the command and apparently there is no package called "lsb-core-ia32". The other package appears to have a bunch of dependencies, around 50. 

So, I installed them all and rebooted the server.

Okay, progress at least. Now when I try to run the server I get the error

```
./cod4_lnxded: error while loading shared libraries: libstdc++.so.6: cannot open shared object file: No such file or directory
```

Now, libstdc++6 appears to be a C++ library, which I have installed. 

Any ideas?

Thanks,
arachan.

---

### Post by Arachan on 2011-08-17
Hello,

Success at last! The suggestion of installed 32-bit libraries got me thinking, and I found a german forum which provided a solution.

Here is the google-translated link:

[http://translate.googleusercontent.com/translate_c?hl=en&rurl=translate.google.com&sl=auto&tl=en&twu=1&u=http://forum.ovh.com/showthread.php%3Ft%3D40888&usg=ALkJrhj_ARdeBDI7bCvkg7fBkl7Rv0U0wg](http://translate.googleusercontent.com/translate_c?hl=en&rurl=translate.google.com&sl=auto&tl=en&twu=1&u=http://forum.ovh.com/showthread.php%3Ft%3D40888&usg=ALkJrhj_ARdeBDI7bCvkg7fBkl7Rv0U0wg)

Thanks everyone for their help, marked as solved.

arachan.

---

### Post by fdrake on 2011-08-17
loged in your server:
```

sudo su
ln -s /usr/lib/gcc/x86_64-pc-linux-gnu/4.4.5/32/libstdc++.so.6 /usr/libstdc++.so.6

```

---

### Post by fdrake on 2011-08-17
i am happy for you ...  :D

---

