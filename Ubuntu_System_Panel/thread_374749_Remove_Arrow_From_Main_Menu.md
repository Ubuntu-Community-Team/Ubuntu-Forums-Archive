---
title: "Remove Arrow From Main Menu?"
date: 2007-03-02
forum: Ubuntu System Panel
---

### Post by brokencrystal on 2007-03-02
I want to recompile Ubuntu (Gnome) from source because I want to remove the arrow on the 'main menu applet' (not usp) that covers my custiom icon.

1. Does anyone know where I can get the source code for Ubuntu's Gnome? I want Ubuntu's version of Gnome, as not to change my Ubuntu too much.

2. Does anyone know what part of the code I need to comment out to remove this arrow? I read how to do it before on the net, but I can't find it now.

3. Can anyone tell me how to recompile it when I am done commenting out this line of code?

4. Is there any way to make this new recompiled verison of Ubuntu as a Ubuntu Install/Live CD so I can install the modified version of Ubuntu on all my other machines?

Thanks in advance...

---

### Post by yabbadabbadont on 2007-03-02
1)
apt-get source packagename

Will get you the source.

apt-get build-dep packagename

Will get you all the required development packages to build that source.

2) Nope.  Try searching with google.  There is probably a patch floating around that does this already.

3)  If you need to ask, maybe you shouldn't be doing it.  :D  (unless you just want to learn how)

4) Probably, but you will need to search to find out how to remaster the cd.  If you created a proper dep package using a higher version number, then it would be the one used.

---

### Post by brokencrystal on 2007-03-02
> **yabbadabbadont said:**
> 
3)  If you need to ask, maybe you shouldn't be doing it.  :D  (unless you just want to learn how)


Yep, I want to learn

---

### Post by yabbadabbadont on 2007-03-02
Good for you.  It's nice to find someone in these forums who is willing to learn.  Seems like lately, most posters want you to drive to their house and do it for them.  :lol:

Anyway, this might answer some of your questions:

[http://ubuntuforums.org/showthread.php?t=51003](http://ubuntuforums.org/showthread.php?t=51003)

---

### Post by brokencrystal on 2007-03-02
"
Anyway, this might answer some of your questions:

[http://ubuntuforums.org/showthread.php?t=51003](http://ubuntuforums.org/showthread.php?t=51003)
"

Thanks for the reply.  It looks like that link explains how to make a .deb package.  I could not find how to compile something like gnome from source.  

I wonder if it is like anything else in Linux?

./configure
make
make config

---

### Post by Prometheus.172214 on 2007-03-03
> **yabbadabbadont said:**
> Seems like lately, most posters want you to drive to their house and do it for them.  :lol:

Ain't that the story everywhere ?

My question: Let me assume that I have some packages installed and configured like a mail client, rss feeds, system settings, netwrok settings etc. Is it possible that I take the config files for all this and then when recompiling the source replace them with the one I want? The idea is to create an unattended installation, so when I reinstall and boot, it shoud have all the settings and configuration already done for me.

How tough and complicated is it?

---

### Post by Malac on 2007-03-03
You could try this :
[http://reconstructor.aperantis.com/](http://reconstructor.aperantis.com/)

It says it can construct a custom Ubuntu install. I haven't looked into it very far but it may fit the bill. :)

---

### Post by brokencrystal on 2007-03-03
> **Malac said:**
> You could try this :
[http://reconstructor.aperantis.com/](http://reconstructor.aperantis.com/)

It says it can construct a custom Ubuntu install. I haven't looked into it very far but it may fit the bill. :)

Yes, I was going to recommend the exact same thing.  I have used this for some time now and it's great!  

Unfortunately, that still doesn't solve my problem though...

I need to recompile Gnome for Ubuntu and include it in the reconstructed version.

---

### Post by yabbadabbadont on 2007-03-03
> **brokencrystal said:**
> Yes, I was going to recommend the exact same thing.  I have used this for some time now and it's great!  

Unfortunately, that still doesn't solve my problem though...

I need to recompile Gnome for Ubuntu and include it in the reconstructed version.

Do you need to rebuild all of Gnome, or just gnome-panel?  It seems to me that it would only be the gnome-panel package that would have to be customized.  Then, like you mentioned earlier, it would probably be a matter of running ./configure with the proper options (./configure --help to see what's available), make, then use the instructions from the link I gave you to build a proper deb package.  (or you could just use checkinstall -D --install=no to create a simple one without dependency information)

---

### Post by HeWhoE on 2007-03-30
Someone here seems to have found which part of the code puts the little black triangle on the menu.  [http://ubuntuforums.org/showpost.php?p=2157523&postcount=3]("http://ubuntuforums.org/showpost.php?p=2157523&postcount=3")

---

