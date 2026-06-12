---
title: "Welcome message before Login prompt... is it possible?"
date: 2008-04-29
forum: Server Platforms
---

### Post by samalex on 2008-04-29
Hi,

How can I setup sshd to show a message when someone connects to my Ubuntu Server before they are prompted for Login?  I know the Banner option in sshd_config shows up after Login is entered and /etc/motd is after they are authenticated, but what about before anything is entered?

This has to be possible, but I'm seeing no way of doing this.  I'd like to have a 'Welcome' message appear before anyone even types their login message.

Thanks--

Alex

---

### Post by encompass on 2008-04-29
I know if you want you can set a custom welcome message in the GDM graphical login screen. look at Settings--- administration... login... I think... and you can set things there...

---

### Post by Dr Small on 2008-04-29
You would want to edit /etc/issue

---

### Post by mam00th on 2008-04-29
> **samalex said:**
> Hi,

How can I setup sshd to show a message when someone connects to my Ubuntu Server before they are prompted for Login?  I know the Banner option in sshd_config shows up after Login is entered and /etc/motd is after they are authenticated, but what about before anything is entered?

This has to be possible, but I'm seeing no way of doing this.  I'd like to have a 'Welcome' message appear before anyone even types their login message.

Thanks--

Alex

I would be intersted in this as well!

---

### Post by mam00th on 2008-04-29
Humm I dont really know since Banner show only after login...

---

### Post by Dr Small on 2008-04-29
As I mentioned before, it is /etc/issue.
You need to enable Banner in /etc/ssh/sshd_config and make sure it points to that file.

Dr Small

---

### Post by mam00th on 2008-04-29
Well I've tried enabling the banner but still dont see anything before the login promt. And yes I did change the /etc/issue

---

### Post by scorp123 on 2008-04-29
> **mam00th said:**
> Well I've tried enabling the banner but still dont see anything before the login promt. And yes I did change the /etc/issue The correct file is: **/etc/issue.net**
/etc/issue is only for local logins.

And this statement has to be set in /etc/ssh/sshd_config:
```
Banner /etc/issue.net
```

And once this is done you have to restart the SSH daemon or the setting will not become active until the next reboot:
```
sudo /etc/init.d/ssh restart
```

---

### Post by Dr Small on 2008-04-29
Ah well, I generally symlink /etc/issue.net to /etc/issue. But I just forgot that.

---

### Post by scorp123 on 2008-04-29
> **Dr Small said:**
> Ah well, I generally symlink /etc/issue.net to /etc/issue. But I just forgot that. There is an advantage in keeping the two apart. For example your /etc/issue could look friendly like this:
```
Ubuntu 7.10 \n \l 


                                  \\\|///
                                \\  ~ ~  //
                                 (  @ @  )
-------------------------------oOOo-(_)-oOOo-----------------------------------

Authorized personnel only. Thank you. 

----------------------------------------Oooo.----------------------------------
                              .oooO     (   )
                              (   )      ) /
                               \ (      (_/
                                \_)

```

... whereas your /etc/issue.net could look unfriendly and uninviting like this: ```

+--------------------------------------------+
|  + + +   A C C E S S  D E N I E D   + + +  |
+--------------------------------------------+
| All traffic, transmissions and protocols   |
| from and to this machine are being logged. |
+--------------------------------------------+

     Your IP address has been recorded.

       Access to this machine is for
      authorized administrators only.
     If you are not an authorized user,
             please leave now.

             You were warned. 
```

Not that it helps one little bit if you have no security whatsoever in place, but it at least might help to keep the script kiddies away. And removing the detailed version information from /etc/issue.net (what OS, what kernel, etc.) is a good idea anyway.

---

### Post by mam00th on 2008-04-29
Well I tried it and the issue.net appear right after the login prompt. Is there some way to make it appear before?

---

### Post by Dr Small on 2008-04-29
Did you restart ssh?
```
sudo /etc/init.d/ssh restart
```

---

### Post by scorp123 on 2008-04-30
> **mam00th said:**
> Well I tried it and the issue.net appear right after the login prompt.  /etc/motd appears after the login prompt. You probably modified that one. /etc/issue.net will appear before. See above. You have to define the "Banner" statement in /etc/ssh/sshd_config

---

### Post by mam00th on 2008-04-30
> **scorp123 said:**
> /etc/motd appears after the login prompt. You probably modified that one. /etc/issue.net will appear before. See above. You have to define the "Banner" statement in /etc/ssh/sshd_config

Well I did restart ssh but here's what happen

Login: (i enter my user name)

The message in /etc/issue.net

Password : ******

MOTD

---

### Post by enigmaniac23 on 2008-04-30
Are you using putty, or are you ssh'ing directly from a terminal?

Mine works as it should from a terminal, but with putty, if I don't configure a Auto Login user name, then I get what you are getting.

---

### Post by mam00th on 2008-04-30
I am using putty so you're saying that it isn't possible to show a message before the login prompt using putty?

---

### Post by moonpup on 2008-04-30
Bottom line, this is just a quirk with putty. I have never been able to get it to display the issue.net file before asking for the username. Recommendation is to email the developer and ask him to implement it correctly.

Like others have said, if you do this from the command line of any nix box or even use the windows ssh tectia client or securecrt from vandyke software you will see that the message displays as it should before asking for the username. Again, it's a putty issue no more... no less.

Hope that helps.

---

### Post by scorp123 on 2008-04-30
> **moonpup said:**
> Bottom line, this is just a quirk with putty. Good to know. Thanks.

---

### Post by mam00th on 2008-04-30
> **moonpup said:**
> Bottom line, this is just a quirk with putty.

Thanks a lot for the info!

---

### Post by samalex on 2008-05-02
Hi everyone,

Yup that's my issue is I'm using Putty.  I guess I was thinking SSH was more alike old-school telnet where you could show a message before login, but I forgot ssh uses usernames abit differently.

Thanks for all the suggestions and replies --

Alex

---

### Post by ghostknife on 2008-05-03
Thanks for the nice issue suggestions scorp123 ;> 

Here's another lame one with play on the popular banner: Trespassers will be sent to Trash

---

### Post by Alien Collective on 2008-05-03
> **scorp123 said:**
> There is an advantage in keeping the two apart. For example your /etc/issue could look friendly like this:
```
Ubuntu 7.10 \n \l 


                                  \\\|///
                                \\  ~ ~  //
                                 (  @ @  )
-------------------------------oOOo-(_)-oOOo-----------------------------------

Authorized personnel only. Thank you. 

----------------------------------------Oooo.----------------------------------
                              .oooO     (   )
                              (   )      ) /
                               \ (      (_/
                                \_)

```

Call me immature, but that's awesome. I'm going to have to put that on my own server. :D

---

### Post by scorp123 on 2008-05-03
> **Alien Collective said:**
> Call me immature, but that's awesome. I'm going to have to put that on my own server. :D I got that one from a really *LARGE* customer site with several 1000 UNIX installations .... seems some of their admins have a very wicked sense of humor. They sometimes also compile their own stuff and replace the standard error messages with stuff of their own, e.g. instead of "segmentation fault - core dumped" or something like that some of their programs will happily report "I made an ooopsie." :)

---

### Post by ghostknife on 2008-05-04
The "I made an oopsie" fits very nice into "core dumped".

Something interesting. Did you know kernel panics are internally to the kernel source referred to as "OOPS" errors?

---

### Post by mic159 on 2009-07-28
Hey guys, i wanna know how to do this.
I know it IS possible and dont tell me its putty's fault, because iv seen it done! although the SSH server was on a RedHat box.

You guys are getting confused because the people saying its working are using username@host, whereas the people aksing the questions are just using host.

I want to know how to do this:

 - SSH to box (NO autologin!!!!!!! ie 192.168.0.3, not username@192.168.0.3)

[Display a message 1]

login as: [enter username]

[Display message 2]

password: [enter password]

[welcome message /etc/motd]

---

### Post by ghostknife on 2009-07-28
As mentioned in the post:
Edit your /etc/ssh/sshd_config file, and uncomment the line:
#Banner /etc/issue.net

To read:
Banner /etc/issue.net

Then /etc/issue.net will be your "pre-login banner".

My pre-login banner on my VPS points to /etc/ssh/login.warn, which is done with:
Banner /etc/ssh/login.warn

Further, putty cannot show this before your login, because putty first establishes the connection, then asks for the username, then continues to the message, where openssh client swaps the last 2 steps around into: establish, message then username.

---

