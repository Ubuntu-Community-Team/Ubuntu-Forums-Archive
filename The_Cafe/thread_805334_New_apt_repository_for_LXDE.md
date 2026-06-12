---
title: "New apt repository for LXDE"
date: 2008-05-23
forum: The Cafe
---

### Post by PCMan on 2008-05-23
Hi all, we have new apt repository for[ LXDE]("http://lxde.org/") now.
There is no update in my personal apt repository for quite a long time because I don't have ubuntu anymore. Ubuntu 8.04 performed poorly on my laptop, and there are a lot of unresolved problems, so I removed ubuntu, and switched to ArchLinux recently.
Fortunately, we found another package maintainer - [michael r < michael.r@spamfreemail.de>]("https://launchpad.net/~michael-r"). He built up a new repo on Launpad PPA of LXDE for us.

For Ubuntu 8.04 hardy
```

deb http://ppa.launchpad.net/lxde/ubuntu hardy main
deb-src http://ppa.launchpad.net/lxde/ubuntu hardy main
```

For Ubuntu 7.10 gutsy
```

deb http://ppa.launchpad.net/lxde/ubuntu gutsy main
deb-src http://ppa.launchpad.net/lxde/ubuntu gutsy main
```

Just do this, and you'll get the latest LXDE (lightweight X11 desktop environment) for Hardy.
```
sudo apt-get update
sudo apt-get install lxde
```

From now on, our official ubuntu repo will be moved to Launchpad PPA service.
Currently, i386, amd64, and lpa packages of the latest LXDE are provided for Hardy. Please upgrade now!!

Alternatively, you can use the repository provided by [Ubuntulite]("http://ubuntulite.tuxfamily.org/") project.
This is a lightweight branch of Ubuntu. They [switched to LXDE in Ubuntulite 0.8 release]("http://ubuntulite.tuxfamily.org/?q=node/96").

Cheers!!

---

### Post by LeoSolaris on 2008-05-27
I was curious about LXDE, so I decided to add the repo to my 8.04 64-bit.

This was the output: 

```
10:31 PM on Tue May 27 leo-laptop: ~$ sudo apt-get install lxde
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  lxde: Depends: lxde-common (>= 0.3.2.1-12~lxde) but it is not going to be installed
E: Broken packages

```

Another question I thought of after looking over your website and Ubuntu's forum... I see that it is possible to change Openbox to Metacity, but I would like to know if it can be changed to Compiz? 

If it can, and the panels are removable, it may be exactly what I am looking for. My entire desktop is an AWN bar and a conky in the background, without the gnome panel, but gnome does throw tantrums about it occasionally.

I am setting up an Arch system, so I have been exploring different set-ups, but none of them run the way I wish... namely, low resources but able to use compiz simply for the AWN bar. The other bars do not have the functionality AWN has in it's new applets. (A Main menu to be precise)

---

### Post by jrusso2 on 2008-05-27
Great, thanks I have been wanting to have a look at LXDE

---

### Post by dustigroove on 2008-05-30
I haven't used all of the LXDE components in their entirety, however LXappearance and LXpanel seem to work well on my system so far, Good stuff!

Cheers,

---

### Post by stlouisubntu on 2008-08-24
> **LeoSolaris said:**
> I was curious about LXDE, so I decided to add the repo to my 8.04 64-bit.

This was the output: 

```
10:31 PM on Tue May 27 leo-laptop: ~$ sudo apt-get install lxde
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  lxde: Depends: lxde-common (>= 0.3.2.1-12~lxde) but it is not going to be installed
E: Broken packages

```

Another question I thought of after looking over your website and Ubuntu's forum... I see that it is possible to change Openbox to Metacity, but I would like to know if it can be changed to Compiz? 

If it can, and the panels are removable, it may be exactly what I am looking for. My entire desktop is an AWN bar and a conky in the background, without the gnome panel, but gnome does throw tantrums about it occasionally.

I am setting up an Arch system, so I have been exploring different set-ups, but none of them run the way I wish... namely, low resources but able to use compiz simply for the AWN bar. The other bars do not have the functionality AWN has in it's new applets. (A Main menu to be precise)




Likewise, I had the broken packages / unmet dependcies error messages
while trying to install LXDE.  I got these errors after doing an apt-get
update following adding the aforementioned gutsy repositories.  The
new ubuntulite will give a "failed" message if one attempts execute
it using anything but hardy.

My successful workaround was to add the Debian Lenny repositories and the
LXDE repositories.  Then do sudo apt-get update, then sudo apt-get install
LXDE.  It will then install with all dependcies met successfully.  (However, I recommend going back and commenting out the Debian Lenny
repos to minimize future conflicts when attempting to install other packages.

The repos I added are as follows:

deb [http://people.linux.org.tw/~andrew/debian/lxde/](http://people.linux.org.tw/~andrew/debian/lxde/) ./ 
deb [http://ftp.nl.debian.org/debian/](http://ftp.nl.debian.org/debian/) lenny main contrib non-free
deb [http://security.debian.org/](http://security.debian.org/) lenny/updates main contrib non-free

I hope this helps someone as it was not an easy solution to find.
Also, the broken packages for Gusty above really should be fixed.
Should it be reported as a bug?

:)

---

### Post by doorknob60 on 2008-08-24
> **stlouisubntu said:**
> Likewise, I had the broken packages / unmet dependcies error messages
while trying to install LXDE.  I got these errors after doing an apt-get
update following adding the aforementioned gutsy repositories.  The
new ubuntulite will give a "failed" message if one attempts execute
it using anything but hardy.

My successful workaround was to add the Debian Lenny repositories and the
LXDE repositories.  Then do sudo apt-get update, then sudo apt-get install
LXDE.  It will then install with all dependcies met successfully.  (However, I recommend going back and commenting out the Debian Lenny
repos to minimize future conflicts when attempting to install other packages.

The repos I added are as follows:

deb [http://people.linux.org.tw/~andrew/debian/lxde/](http://people.linux.org.tw/~andrew/debian/lxde/) ./ 
deb [http://ftp.nl.debian.org/debian/](http://ftp.nl.debian.org/debian/) lenny main contrib non-free
deb [http://security.debian.org/](http://security.debian.org/) lenny/updates main contrib non-free

I hope this helps someone as it was not an easy solution to find.
Also, the broken packages for Gusty above really should be fixed.
Should it be reported as a bug?

:)

***NO! BAD! NEVER MIX DEBIAN AND UBUNTU REPOSITORIES! IT CAN BREAK YOUR SYSTEM!*** Sorry for the caps, but it's a bad idea, because even though Ubuntu is based off Debian, they aren't binary compatible, and mixing repositories is a good way to screw up your system. Just don't do it. Ever. </disclaimer>

---

### Post by stlouisubntu on 2008-08-26
> **doorknob60 said:**
> ***NO! BAD! NEVER MIX DEBIAN AND UBUNTU REPOSITORIES! IT CAN BREAK YOUR SYSTEM!*** Sorry for the caps, but it's a bad idea, because even though Ubuntu is based off Debian, they aren't binary compatible, and mixing repositories is a good way to screw up your system. Just don't do it. Ever. </disclaimer>


My proposed work around worked fine for me.  Also, it was the ONLY way
I was able to get LXDE installed on my gusty installation.  Immediately
after I completed the successful LXDE install, I removed (or at least 
commented out) those three repos I mentioned followed by an apt-get update.
My system did not break, but now works fine (with LXDE.)  I did have
to uninstall Thunar as it conflicted with PCMAN.  Respectfully, it appears
that your reasoning is not sound.  Based upon your thinking it would also
be bad to download and dpkg -i .deb files (given that one does need to 
be careful when doing so but it will not normally break one's system
if one does not attempt to install something really wrong.)

If my workaround is BAD, please propose another one (for a gusty user)
short of upgrading to hardy (gutsy is still well within its 18 month
support period.)  Waiting for the above gusty repos to be fixed could
take considerably longer that one wants to wait to install LXDE.  My 
workaround can be used to install it within 10 minutes or less.

Also, couldn't help but notice that you are a Lenny user.  Don't you mind
if we ubuntu users tap into your repos for a quick workaround fix?
(Kidding.)  :)

Respectfully,

---

### Post by n2stc on 2009-03-27
> **stlouisubntu said:**
> Likewise, I had the broken packages .......
I hope this helps someone as it was not an easy solution to find.
Also, the broken packages for Gusty above really should be fixed.
Should it be reported as a bug?

:)

Thanks it worked for me too.  I'll be sure to comment them out.  I REALLY like LXDE so far.  It seems like the best compromise between appearance & speed.  THANKS!

---

