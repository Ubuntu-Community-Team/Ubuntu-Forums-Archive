---
title: "Login panel is worse from security view point"
date: 2010-01-19
forum: Security
---

### Post by yilin on 2010-01-19
ubuntu 9.10 login panel is worse with respect to ubuntu 8 since now all the users with names are shown without a way to hide them!

Why don't keep the old way at least as an option?

---

### Post by bodhi.zazen on 2010-01-19
> **yilin said:**
> ubuntu 9.10 login panel is worse with respect to ubuntu 8 since now all the users with names are shown without a way to hide them!

Why don't keep the old way at least as an option?

I understand what you are saying, but if you think about it, it really does not matter.

If someone has physical access, a log in screen without user names will not really slow them down much anyways.

The problems you have with physical access overshadow the listing of user names on the log in screen.

With that said, yes I hope methods of theming the log in screen becomes much much easier in the near future.

---

### Post by Denestria on 2010-01-19
I don't appreciate having my userlist plastered across the login screen against my wishes either.  I got rid of it on my netbook.

```
sudo -u gdm gconftool-2 --set --type boolean /apps/gdm/simple-greeter/disable_user_list true
```

---

### Post by CharlesA on 2010-01-19
> **Denestria said:**
> I don't appreciate having my userlist plastered across the login screen against my wishes either.  I got rid of it on my netbook.

```
sudo -u gdm gconftool-2 --set --type boolean /apps/gdm/simple-greeter/disable_user_list true
```

That's very handy.

Thanks! :D

---

### Post by mcook2 on 2010-06-20
I am in the process of trying out Ubuntu 10.4 (upgrading from 8.04) and I agree that the "Login panel is worse from security view point", in my case 'cos I don't want to see the list however long or short it might be, and don't mind typing in my userID. I was surprised to find that the "Hide user list" option is now gone from the applet at System / Login Screen on 10.4.   
 
Looking into this, I found quite a long thread on the subject for Karmic Koala [http://ubuntuforums.org/showthread.php?t=1287054&page=1]("http://ubuntuforums.org/showthread.php?t=1287054&page=1"). That thread has been closed for a while. It contains a lot of discussion, but I gather that the main reason this was changed was that GDM was changed and various little applets like this one just haven't caught up yet.

I can live with that. It's "No biggie" in my Home Office tho' it would be in various places I've worked. I still wanted to change it anyway.

I followed what was done, tried it out, and even got it work but only using the gconf-editor GUI as follows:

To start with, I went:

 - press ALT+F2 and type
 - gksu gconf-editor
 - then navigate to /apps/gdm/simple-greeter
 - and check disable_user_list.

However, this didn't work after Logout/Login, nor after a reboot, , so I fiddled with it a bit more and realized that I probably needed to do "Set as Mandatory":

 - Go Applications/System Tools/Configuration Editor
 - Select /apps/gdm/simple-greeter
 - Check disable_user_list
 - Then right mouse click on the key name ... 
 - and click "Set as Mandatory".

"Set Default" is also an option. This makes sense 'cos you can set these keys at various levels, and it's the system level that you want to change.

 - It should at this point ask for your Admin password
 - Close the editor using File/Close
 - Log off and it should be working as you want (i.e. no user name list). [P.S. do you have to reboot?]

Here's a picture of my gconf-editor while doing this:

[IMG]http://skyprod.net/~mcook/Ubuntu/Screenshot-Configuration Editor%20-%20simple-greeter.png[/IMG]

Note that under Key Documentation it says "! This key is not writable".

Of course you can also sudo gconf-editor to start the GUI from the command line but I think you probably still have to "Set as Mandatory" or "Set as Default" in the GUI in order to get pleasing results. I'm not 100% certain of this, but the above works for me using gconf-editor only.   

I also looked into whether or not the 100% command line solution might now require some extra switch in order to select Mandatory or Default. I didn't find out anything definite yet.  After my change /etc/gconf/gconf.xml.mandatory/%gconf-tree.xml says:

```

<?xml version="1.0"?>
<gconf>
        <dir name="apps">
                <dir name="gdm">
                        <dir name="simple-greeter">
                                <entry name="disable_user_list" mtime="1277021518" type="bool" value="true"/>
                        </dir>
                </dir>
        </dir>
</gconf>

```

And /etc/gconf/gconf.xml.default/%gconf-tree.xml says the same.

Finally, I did try:

```

sudo -u gdm gconftool-2 --set --type boolean /apps/gdm/simple-greeter/disable_user_list false

```

And I got this message:

> 
Error setting value: Cannot overwrite existing read-only value: Value for `/apps/gdm/simple-greeter/disable_user_list' set in a read-only source at the front of your configuration path


This is on Ubuntu Desktop 10.4 where ```
uname -a
``` says:

> 
Linux cara 2.6.32-22-generic #36-Ubuntu SMP Thu Jun 3 22:02:19 UTC 2010 i686 GNU/Linux
 

So, it gets curiouser and curiouser, but at least I have the setting I want, and I used gconf-editor to do it, and now i have written it up so I'll be able to remember it.

Is this bug or a feature?  Anybody?

Have a nice day,

---

### Post by yilin on 2010-06-23
Thanks mcook2. Very good findings!

---

