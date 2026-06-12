---
title: "Remote access"
date: 2007-06-05
forum: System76 Support
---

### Post by riseringseeker on 2007-06-05
I am in the habit of being able to use various programs via ssh on the desktop from my laptop, where ever in the world my laptop (and I) are at the time.  I have yet to be able to do so with the Darter, and though I was able to use programs (say pam) the other way - from desktop to laptop - I now am unable to do so either way.

If anyone can help me figure out what file to edit (and obviously how!) I would very much appreciate it.  The error message I get trying to run a program via ssh (Darter to Desktop) is:

```

userl@ubuntu:~$ nautilus &
[1] 18898
userl@ubuntu:~$ cannot open display: 

```

I was told that VNC was broken in Feisty, but that must have been via an update, as I was able to use it once - more or less as an experiment - but am currently unable to.

Using ssh worked just fine for me, and has much less overhead than running a full VNC session, and runs faster, especially from the other side of the world

---

### Post by tedrampart on 2007-06-06
there's using

```
 $ ssh -X user@hostname 
```  to load the application on your screen, its called port forwarding.  

so applications running on the computer you logged into over ssh will display on the machine you're using.

check ```
 $ man ssh 
``` for a description of the option in ssh.  you have to add it when you log into the remote computer.

edit - also, I use "terminal server client" in Applications > Internet > terminal server client to remote desktop the system at my work.  I just choose VNC from the protocol drop down option and it works fine.  I'm also in feisty.

---

### Post by snoop on 2007-06-06
I personally love using nomachine (NX or freeNX) easy to use and is tunnelled over ssh.

---

### Post by riseringseeker on 2007-06-06
> **tedrampart said:**
> there's using

```
 $ ssh -X user@hostname 
```  to load the application on your screen, its called port forwarding.  

so applications running on the computer you logged into over ssh will display on the machine you're using.

Did I say something that made you think I did not know about port forwarding?  Also, with ForwardX11/X11Forwarding set to yes in ssh_config, it is superfluous.

> check ```
 $ man ssh 
``` for a description of the option in ssh.  you have to add it when you log into the remote computer.

Well, since I had been doing it for several years **without** adding a Y or X, I question the above statement, besides, as it says in the manpage:

[quote=manpage]

 -X         Enables X11 forwarding.  [b]This can also be specified on a per-host
             basis in a configuration file.[/b]

             
[/quote]

(added emphasis is mine)

---

### Post by tedrampart on 2007-06-07
> **riseringseeker said:**
> Did I say something that made you think I did not know about port forwarding?


I was just trying to help based on what I know.  you didnt say you knew about it, so why not suggest it.  no need to be hostile.

---

### Post by snoop on 2007-06-07
> **riseringseeker said:**
> Did I say something that made you think I did not know about port forwarding?  Also, with ForwardX11/X11Forwarding set to yes in ssh_config, it is superfluous.



Well, since I had been doing it for several years **without** adding a Y or X, I question the above statement, besides, as it says in the manpage:



(added emphasis is mine)

Since you seem to know so much, why ask for help?

---

### Post by riseringseeker on 2007-06-09
> **tedrampart said:**
> I was just trying to help based on what I know.  you didnt say you knew about it, so why not suggest it.  no need to be hostile.

I guess saying I "was in the habit of using ssh..." wasn't really clear enough.  

As far as being hostile, I ask for understanding in that I have had an ADHD kid living here for the last several days.  I should take a few deep breaths, and count to 100 before posting here.

---

### Post by riseringseeker on 2007-06-09
> **snoop said:**
> Since you seem to know so much, why ask for help?

If you are just going to suggest reading a man page, or say "hey it works for me", why do you respond?

---

### Post by snoop on 2007-06-10
> **riseringseeker said:**
> If you are just going to suggest reading a man page, or say "hey it works for me", why do you respond?

I am not going to suggest you read a man page, you apparently already have. As to what I said, it was meant to make you realize that you are asking for help by posting the question, no need to get snappy.

We all have bad days, no worries :)

---

### Post by riseringseeker on 2007-06-12
I have tried to run various programs remotely using ssh, and some give error messages, some don't.  When I ran Mandriva on the old laptop and the same desktop I now have, after editing ssh_config/sshd_config to allow X11 forwarding, I was able to run "gui" apps by doing the following:

```
user@laptop~$ssh <desktop_ip_address>
Enter passphrase for key '/home/user/.ssh/id_rsa': 

user@desktop~$ nautilus &

```

It would then show the process ID and in a moment, open the app on the screen on the laptop.  (The ampersand puts it in the background allowing use of the terminal again)

Now when I try it I get the following error messages

```
userl@desktop:~$ nautilus &
[1] 6333
userl@desktop:~$ cannot open display: 
Run 'nautilus --help' to see a full list of available command line options.

[1]+  Exit 1                  nautilus
user@desktop:~$ konqueror &
[1] 6334
user@desktop:~$ konqueror: cannot connect to X server localhost:0.0

[1]+  Exit 1                  konqueror
user@desktop:~$ gaim &
[1] 6335
user@desktop:~$ 
(gaim:6335): Gdk-CRITICAL **: gdk_display_get_name: assertion `GDK_IS_DISPLAY (display)' failed
Gaim 2.0.0beta6

** (gaim:6335): WARNING **: cannot open display: unset

[1]+  Exit 1                  gaim
user@desktop:~$ skype &
[1] 6336
user@desktop:~$ 
[1]+  Exit 1                  skype
user@desktop:~$ ooffice -writer &
[1] 6337
user@desktop:~$ Failed to open display
/usr/lib/openoffice/program/soffice.bin X11 error: Can't open display: localhost:0.0
   Set DISPLAY environment variable, use -display option
   or check permissions of your X-Server
   (See "man X" resp. "man xhost" for details)

[1]+  Done                    ooffice -writer

```

All of the these (except openoffice) I had run using Mandriva, and see no reason why they are not working now.  On some of the above, the process just seemed to die, on others, it persisted (though did not open) and required a Ctrl-C to stop it.  I am looking through the recommended man pages to see what there is to see, but if someone can give a hand, I would appreciate it.

---

### Post by thomasaaron on 2007-06-12
I remembered reading about this in Beginning Ubuntu Linux -- From Novice to Professional.
So, I just opened it and it recommends the -X switch.

ssh -X <username>@<IP address>

After this, you would type in:

**gnome-session**


(You also need to set your permissions in System > Pref > Remote Desktop

---

### Post by riseringseeker on 2007-06-12
> **thomasaaron said:**
> I remembered reading about this in Beginning Ubuntu Linux -- From Novice to Professional.
So, I just opened it and it recommends the -X switch.

ssh -X <username>@<IP address>

After this, you would type in:

**gnome-session**

```
user@laptop-$ ssh -X user@<desktop_ip>
Enter passphrase for key '/home/user/.ssh/id_rsa': 

user@desktop:~$ gnome-session

(gnome-session:5280): Gtk-WARNING **: cannot open display: 

```
Does not seem to work.  The "-X", or, in the case of trusted hosts, "-Y" is not needed if X11Forwarding/ForwardX11/ForwardAgent are set to yes in ssh_config and sshd_config, (which they are on both machines in question) but putting one of them there won't hurt anything, but in this case at least, it's not helping either.


> (You also need to set your permissions in System > Pref > Remote Desktop

That seems to be pretty much about VNC, which I believe you said was broken in Feisty.  I am not trying to load up the whole desktop here, but simply run one program.   This should work no differently than opening a terminal on your machine and typing "nautilus &" 

I can find no where in System->Preferences->Remote Desktop to do other than to set a password, nothing about permissions per se  - am I missing something?

---

### Post by thomasaaron on 2007-06-27
OK, I don't know if this helps you, but I am able to connect with my remote desktop using the following command:

vncviewer 192.168.1.103:0

This prompts me for the password (which is set in System > Preferences > Remote Desktop.

Of course this is via my wireless connection within my own house. I've not tried it over the Internet from work yet. I'll try that tomorrow.

Best,
Tom

---

### Post by riseringseeker on 2007-06-30
> **thomasaaron said:**
> OK, I don't know if this helps you, but I am able to connect with my remote desktop using the following command:

vncviewer 192.168.1.103:0

This prompts me for the password (which is set in System > Preferences > Remote Desktop.

Of course this is via my wireless connection within my own house. I've not tried it over the Internet from work yet. I'll try that tomorrow.

Best,
Tom

Obviously I have failed to ask the question in a way that will get the reply I am after.

Sorry about the delay in replying, but have just been around the world backwards, and am trying to get circadian rhythms to some semblance of normalcy, before I am off again today to screw them back up.

I am not trying, nor do I really wish to run the entire desktop remotely. What I am attempting to do is run a single application remotely.  Bottom line is that I want to be able to ssh into my desktop at home, and run one single gui application on it.

I may have gotten an answer from a friend of mine that has been running Linux far longer, and more intensely than I ever will.  He suggests the difference how GDM behaves, and suggests that once I get home, to try running "xhost +" as a command line argument then restart the xserver.  Seems GDM by default "protects" itself by not allowing other hosts to connect to the xserver.

Since I just got extended again, it will be a while before I am able to try this.

---

### Post by KeighleHawk on 2007-07-12
from another thread:

[http://ubuntuforums.org/showthread.php?t=446725&highlight=xhost&page=2](http://ubuntuforums.org/showthread.php?t=446725&highlight=xhost&page=2)

The trick was in setting on your local machine (the one you want to display TO):

System -> Administration -> Login Window -> Security -> Deny TCP Connections to Xserver

to OFF.  Then restart your local window manager/xserver or just reboot. 

After that, ssh with X Forwarding (as you mentioned) to your remote desktop (at home), set your DISPLAY variable to the correct IP address:0.0 of your local machine and execute your command.

Note:  you will also have to open an xterm on your local machine and type 'xhost +' or some more secure form of that and/or make a permanent setup which file name escapes me at the moment...

P.S.  This has irritated me for some time and I only just now found the above mentioned thread with the answer, so I feel your pain...

---

### Post by riseringseeker on 2007-09-12
> **KeighleHawk said:**
> from another thread:

[http://ubuntuforums.org/showthread.php?t=446725&highlight=xhost&page=2](http://ubuntuforums.org/showthread.php?t=446725&highlight=xhost&page=2)

The trick was in setting on your local machine (the one you want to display TO):

System -> Administration -> Login Window -> Security -> Deny TCP Connections to Xserver

to OFF.  Then restart your local window manager/xserver or just reboot. 

After that, ssh with X Forwarding (as you mentioned) to your remote desktop (at home), set your DISPLAY variable to the correct IP address:0.0 of your local machine and execute your command.

Note:  you will also have to open an xterm on your local machine and type 'xhost +' or some more secure form of that and/or make a permanent setup which file name escapes me at the moment...

P.S.  This has irritated me for some time and I only just now found the above mentioned thread with the answer, so I feel your pain...

That (mostly) did it!  I can now ssh into the desktop and run most programs anyway, I get a slew of error messages, and can't run a few at all, but can the ones I want/need to.

Thanks

---

