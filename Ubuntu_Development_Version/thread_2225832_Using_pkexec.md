---
title: "Using pkexec"
date: 2014-05-23
forum: Ubuntu Development Version
---

### Post by grahammechanical on 2014-05-23
I have opened this thread because gksu is depreciated and as some of us are finding out gksu sometimes gets broken for some of us. I am now thinking that it is sensible to switch to using pkexec. It is not a replacement for gksu but it can be used to give root privileges to certain applications but we need to create a policy file for those applications.

Ubuntu comes with a set of policies and we find them in /usr/share/polkit-1/actions/. We can follow the pattern used in those policies to create policies ourselves. This is a policy for Gedit that someone in U+1 provided about a year ago. So, I am not claiming credit for this.

1) create this file

/usr/share/polkit-1/actions/com.ubuntu.gedit.policy

2) put in the file this code

```

<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE policyconfig PUBLIC
 "-//freedesktop//DTD PolicyKit Policy Configuration 1.0//EN"
 "http://www.freedesktop.org/standards/PolicyKit/1.0/policyconfig.dtd">
<policyconfig>
  <vendor>gedit</vendor>
  <vendor_url>gedit</vendor_url>
  <icon_name>accessories-text-editor</icon_name>
  <action id="org.freedesktop.policykit.pkexec.gedit">
   <description>Run "gedit"</description>
   <message>Authentication is required to run Text Editor</message>
   <defaults>
     <allow_any>auth_admin</allow_any>
     <allow_inactive>auth_admin</allow_inactive>
     <allow_active>auth_admin</allow_active>
   </defaults>
     <annotate key="org.freedesktop.policykit.exec.path">/usr/bin/gedit</annotate>
     <annotate key="org.freedesktop.policykit.exec.allow_gui">true</annotate>
   </action>  
</policyconfig>

```
Now we can launch Gedit with root privileges using
```
pkexec gedit
```
By following that pattern I have come up with this for nautilus

File name /usr/share/polkit-1/actions/com.ubuntu.nautilus.policy
```

<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE policyconfig PUBLIC
 "-//freedesktop//DTD PolicyKit Policy Configuration 1.0//EN"
 "http://www.freedesktop.org/standards/PolicyKit/1.0/policyconfig.dtd">
<policyconfig>
  <vendor>nautilus</vendor>
  <vendor_url>nautilus</vendor_url>
  <icon_name>system-file-manager</icon_name>
  <action id="org.freedesktop.policykit.pkexec.nautilus">
   <description>Run "nautilus"</description>
   <message>Authentication is required to run File Manager</message>
   <defaults>
     <allow_any>auth_admin</allow_any>
     <allow_inactive>auth_admin</allow_inactive>
     <allow_active>auth_admin</allow_active>
   </defaults>
     <annotate key="org.freedesktop.policykit.exec.path">/usr/bin/nautilus/annotate>
     <annotate key="org.freedesktop.policykit.exec.allow_gui">true</annotate>
   </action>  
</policyconfig>

```
```
pkexec nautilus
```

Make use of it if you will and add to the thread any policies that you come up with that would be useful to a Ubuntu development tester.

Regards

---

### Post by Elfy on 2014-05-23
should > <annotate key="org.freedesktop.policykit.exec.allow_gui">**tru e**</annotate> be 
> <annotate key="org.freedesktop.policykit.exec.allow_gui">**true**</annotate>
 Just mentioning that.

Playing with one for mousepad - got an issue, will look later when I've more time

```
pkexec mousepad

(mousepad:4380): Mousepad-ERROR **: Cannot open display: 
Trace/breakpoint trap
```

Edit thunar gets the same Cannot open display error
Thanks for thinking about a thread for this :)

---

### Post by zika on 2014-05-23
You've made me play with **pkexec** (Trusty is the onla version I have at hand here where i am) and:```
pkexec env DISPLAY=$DISPLAY XAUTHORITY=$XAUTHORITY gedit /etc/rc.local
```works where else I get```
~$ pkexec gedit /etc/rc.local
error: XDG_RUNTIME_DIR not set in the environment.
Unable to init server: Could not connect: Connection refused
(gedit:30178): Gtk-WARNING **: cannot open display: 

```...
Will investigate further, working line I derived from reading manual... ;)
Update&#8321;:
Alias:```
alias pkx='pkexec env DISPLAY=$DISPLAY XAUTHORITY=$XAUTHORITY $i'
```works nicely```
pkx gedit /etc/rc.local
```without significant changes (better to say witout any) to any system files...
This would be my contribution to: &#8222;Using pkexec&#8220;... ;)
Update&#8322;:```
~$ pkx nautilus
(nautilus:1236): Gtk-WARNING **: Failed to register client: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.
```(No Samba installed on this machine with reason...)
```
~$ gksu nautilus
```like knife through butter... ;)

---

### Post by mc4man on 2014-05-23
@ grahammechanical - 
As mentioned before it's better practice if posting something for others to copy to use a code box instead of quote so you maintain formatting
May not matter in this case, eventually will, -  as ex. this is the policy I've included in nautilus's source for some time - 

```
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE policyconfig PUBLIC
 "-//freedesktop//DTD PolicyKit Policy Configuration 1.0//EN"
 "http://www.freedesktop.org/standards/PolicyKit/1/policyconfig.dtd">
<policyconfig>

  <action id="com.ubuntu.pkexec.nautilus">
    <message gettext-domain="nautilus">Authentication is required to run nautilus as root</message>
    <icon_name>system-file-manager</icon_name>
    <defaults>
      <allow_any>no</allow_any>
      <allow_inactive>no</allow_inactive>
      <allow_active>auth_admin</allow_active>
    </defaults>
    <annotate key="org.freedesktop.policykit.exec.path">/usr/bin/nautilus</annotate>
    <annotate key="org.freedesktop.policykit.exec.allow_gui">true</annotate>
  </action>

</policyconfig>
```

As far as a failure "open display:", that sometimes happens on 1st use. A reboot should resolve.
The "Nautilus-Share-Message" message is from having nautilus-share installed & sharing not set up. The package can be removed if not using.

The 'The name org.gnome.SessionManager was not provided by any .service files' message is somewhat common & of no importance.

---

### Post by ventrical on 2014-05-23
> **grahammechanical said:**
> I have opened this thread because gksu is depreciated and as some of us are finding out gksu sometimes gets broken for some of us. I am now thinking that it is sensible to switch to using pkexec. It is not a replacement for gksu but it can be used to give root privileges to certain applications but we need to create a policy file for those applications.

Ubuntu comes with a set of policies and we find them in /usr/share/polkit-1/actions/. We can follow the pattern used in those policies to create policies ourselves. This is a policy for Gedit that someone in U+1 provided about a year ago. So, I am not claiming credit for this.

1) create this file

/usr/share/polkit-1/actions/com.ubuntu.gedit.policy

2) put in the file this code

Now we can launch Gedit with root privileges using



No there..

```

ventrical@ventrical-desktop:~$ pkexec gedit
error: XDG_RUNTIME_DIR not set in the environment.

(gedit:4518): Gtk-WARNING **: cannot open display: 
ventrical@ventrical-desktop:~$ 


```

but I'll edit..and try again.

---

### Post by ventrical on 2014-05-23
> **mc4man said:**
> @ grahammechanical - 
As mentioned before it's better practice if posting something for others to copy to use a code box instead of quote so you maintain formatting
May not matter in this case, eventually will, -  as ex. this is the policy I've included in nautilus's source for some time - 

```
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE policyconfig PUBLIC
 "-//freedesktop//DTD PolicyKit Policy Configuration 1.0//EN"
 "http://www.freedesktop.org/standards/PolicyKit/1/policyconfig.dtd">
<policyconfig>

  <action id="com.ubuntu.pkexec.nautilus">
    <message gettext-domain="nautilus">Authentication is required to run nautilus as root</message>
    <icon_name>system-file-manager</icon_name>
    <defaults>
      <allow_any>no</allow_any>
      <allow_inactive>no</allow_inactive>
      <allow_active>auth_admin</allow_active>
    </defaults>
    <annotate key="org.freedesktop.policykit.exec.path">/usr/bin/nautilus</annotate>
    <annotate key="org.freedesktop.policykit.exec.allow_gui">true</annotate>
  </action>

</policyconfig>
```

As far as a failure "open display:", that sometimes happens on 1st use. A reboot should resolve.
The "Nautilus-Share-Message" message is from having nautilus-share installed & sharing not set up. The package can be removed if not using.

The 'The name org.gnome.SessionManager was not provided by any .service files' message is somewhat common & of no importance.


This works  just as well as gksu.

@graham,

Thanks for researching this and making a thread of it.

Regards.

---

### Post by zika on 2014-05-23
> **ventrical said:**
> ```

ventrical@ventrical-desktop:~$ pkexec gedit
error: XDG_RUNTIME_DIR not set in the environment.

(gedit:4518): Gtk-WARNING **: cannot open display: 
ventrical@ventrical-desktop:~$ 


```but I'll edit..and try again.Did You try before any editing```
pkexec env DISPLAY=$DISPLAY XAUTHORITY=$XAUTHORITY gedit
```...?
(As I've suggested above...)

---

### Post by Elfy on 2014-05-23
Got thunar and mousepad now
 Mousepad
```
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE policyconfig PUBLIC
 "-//freedesktop//DTD PolicyKit Policy Configuration 1.0//EN"
 "http://www.freedesktop.org/standards/PolicyKit/1/policyconfig.dtd">
<policyconfig>

  <action id="com.ubuntu.pkexec.mousepad">
    <message gettext-domain="mousepad">Authentication is required to run mousepad as root</message>
    <icon_name>Text Editor</icon_name>
    <defaults>
      <allow_any>no</allow_any>
      <allow_inactive>no</allow_inactive>
      <allow_active>auth_admin</allow_active>
    </defaults>
    <annotate key="org.freedesktop.policykit.exec.path">/usr/bin/mousepad</annotate>
    <annotate key="org.freedesktop.policykit.exec.allow_gui">true</annotate>
  </action>

</policyconfig>
```

Thunar
```
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE policyconfig PUBLIC
 "-//freedesktop//DTD PolicyKit Policy Configuration 1.0//EN"
 "http://www.freedesktop.org/standards/PolicyKit/1/policyconfig.dtd">
<policyconfig>

  <action id="com.ubuntu.pkexec.thunar">
    <message gettext-domain="thunar">Authentication is required to run thunar as root</message>
    <icon_name>system-file-manager</icon_name>
    <defaults>
      <allow_any>no</allow_any>
      <allow_inactive>no</allow_inactive>
      <allow_active>auth_admin</allow_active>
    </defaults>
    <annotate key="org.freedesktop.policykit.exec.path">/usr/bin/thunar</annotate>
    <annotate key="org.freedesktop.policykit.exec.allow_gui">true</annotate>
  </action>

</policyconfig>
```

---

### Post by ventrical on 2014-05-23
> **zika said:**
> Did You try before any editing```
pkexec env DISPLAY=$DISPLAY XAUTHORITY=$XAUTHORITY gedit
```...?
(As I've suggested above...)

 I didn't see that. That's perfect   .. and no verbose msgs either after I closed open gedit.:) That's all I really need in most cases.

```




ventrical@ventrical-desktop:~$ pkexec env DISPLAY=$DISPLAY XAUTHORITY=$XAUTHORITY gedit
ventrical@ventrical-desktop:~$ 


```

---

### Post by ventrical on 2014-05-23
I made it executable and now all I have to do is enter ,

```


rootgedit


```

in terminal . (That is what I named the file). But you have to do this first..

```

ventrical@ventrical-desktop:~$ sudo chmod +x /usr/local/bin/rootgedit
##makes the text file rootgedit executable

[sudo] password for ventrical: 
ventrical@ventrical-desktop:~$ sudo updatedb
##updates the datatbase

ventrical@ventrical-desktop:~$ rootgedit
## executes  the terminal code 


ventrical@ventrical-desktop:~$ 


```


Simply , rootgedit executes,

```

pkexec env DISPLAY=$DISPLAY XAUTHORITY=$XAUTHORITY gedit

```

---

### Post by Sworddragon on 2014-05-24
If pkexec wouldn't require to permanently run the polycikit process in the background then I would think about to replace gksu with it.

---

### Post by zika on 2014-05-24
> **ventrical said:**
> I made it executable and now all I have to do is enter ,

```


rootgedit


```

in terminal . (That is what I named the file). But you have to do this first..

```

ventrical@ventrical-desktop:~$ sudo chmod +x /usr/local/bin/rootgedit
##makes the text file rootgedit executable

[sudo] password for ventrical: 
ventrical@ventrical-desktop:~$ sudo updatedb
##updates the datatbase

ventrical@ventrical-desktop:~$ rootgedit
## executes  the terminal code 


ventrical@ventrical-desktop:~$ 


```


Simply , rootgedit executes,

```

pkexec env DISPLAY=$DISPLAY XAUTHORITY=$XAUTHORITY gedit

```You must have missed my advice about alias...
Updatedb was needed because...?

---

### Post by ventrical on 2014-05-24
> **zika said:**
> You must have missed my advice about alias...
Updatedb was needed because...?


 :) ..

 Honestly .. I'm just experimenting with stuff here.  The updatedb was  for a windows launcher. I am working on making that script a Unity panel launch item. I'm just trying different things. Thanks for asking.

From:


[https://help.ubuntu.com/community/HowToAddaLauncher](https://help.ubuntu.com/community/HowToAddaLauncher)



> 


[LIST=1]
[*]Make the file executable by typing the following in the terminal:
sudo chmod +x /usr/local/bin/sampleprogram 
[*]In the *Create Launcher* window, fill Command with /usr/local/bin/sampleprogram (or just *sampleprogram*, but be sure to update your database before that by typing the following in the terminal:
sudo updatedb 
[/LIST]


I'll have to re-read your advice about alias.

Regards..

---

### Post by ventrical on 2014-05-24
> **zika said:**
> You've made me play with **pkexec** (Trusty is the onla version I have at hand here where i am) and:```
pkexec env DISPLAY=$DISPLAY XAUTHORITY=$XAUTHORITY gedit /etc/rc.local
```works where else I get```
~$ pkexec gedit /etc/rc.local
error: XDG_RUNTIME_DIR not set in the environment.
Unable to init server: Could not connect: Connection refused
(gedit:30178): Gtk-WARNING **: cannot open display: 

```...
Will investigate further, working line I derived from reading manual... ;)
Update&#8321;:
Alias:```
alias pkx='pkexec env DISPLAY=$DISPLAY XAUTHORITY=$XAUTHORITY $i'
```works nicely```




Oh... so does the above assign pkx to pkexec (I would assume)? If I understand you correctly, I would not need to make a shell script then.

Regards..

Edit:

Ok.. yes .. very kewl zika ! :)

[CODE]
ventrical@ventrical-desktop:~$ pkx gedit
ventrical@ventrical-desktop:~$ pkx nautilus

(nautilus:4221): Gtk-WARNING **: Failed to register client: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

^C
ventrical@ventrical-desktop:~$ 


```

---

### Post by grahammechanical on 2014-05-24
Here is some useless information from my experiments.

If I run nautilus from the terminal I do not get Gtk-WARNING when the application loads or Glib-CRITICAL when the application closes.
If I run sudo nautilus or pkexec nautilus I get both Gtk-WARNING when the application loads and Glib-CRITICAL when the application closes.
if I run gksudo nautilus or gksu nautilus I do not get Gtk-WARNING when the application loads but I do get Glib-CRITICAL when the application closes.

As I said, useless information. Some more useless information.

I do not get any of those messages whichever way I run Gedit from the terminal. Not even with pkexec gedit. So, the script that I used to create a Gedit Polkit policy is a fine script. And there is an already existing Polkit policy for Synaptic. There are no error messages when using pkexec synaptic.

We are using a Polkit policy to allow an application to run with administrator privileges. The official Polkit policies are used to limit the power of certain utilities. For example, USB Creator is not allowed to install the bootloader, format the device, write an image to the device, mount the device. Which makes it a useless utility until it receives admin authorisation. 

```

 <defaults>
      <allow_any>no</allow_any>
      <allow_inactive>no</allow_inactive>
      <allow_active>auth_admin_keep</allow_active>
    </defaults>

```

---

### Post by zika on 2014-05-24
> **grahammechanical said:**
> If I run ```
sudo nautilus
``` or ```
pkexec nautilus
``` I get both Gtk-WARNING when the application loads and Glib-CRITICAL when the application closes.To repeat: [COLOR=#800080]using ```
sudo nautilus
```can (now even more than before) get You in the position to make more damage than any warning can proclaim... [/COLOR];)
[COLOR=#696969]Disclaimer: I am not writing this to warn You but to warn anyone else just casually reading this...[/COLOR] ;)
Why am I pro alias (and using pkexec just with switches, naming alias so that no new command will be named that way) and not pro devoting myself to (as far as I can see quite OK script You wrote? Just because all this is a work in progress and once You write that script and forget about it, You can get into trouble without even remembering what You did change ad how that affect new stuff that is rolling from behind the hill... Not to mention that upgrade of some package could/will destroy that setting even without warning You about that... Been there, done that... ;)

---

### Post by grahammechanical on 2014-05-24
@zika

I do not disagree with anything that you have written. I notice this from wikipedia

> [COLOR=#252525][FONT=sans-serif]Polkit has been criticized for contravening the [/FONT][/COLOR][Unix philosophy]("http://en.wikipedia.org/wiki/Unix_philosophy")[COLOR=#252525][FONT=sans-serif] of "doing one task and doing it well". The criticism is applied because Polkit has a primary task of restricting root processes as an "authority". A secondary (but easily mistaken for its primary) task is to provide the "authorization", allowing users to obtain temporary privileges. This criticism has been contested by Polkit's developer.[/FONT][/COLOR]

I am not concerned about Unix ethics. What really does worry me is the fact that in other sections of the forum users are often advised to edit system files. But gksu is no longer installed by default and if it gets broken beyond repair at some point in the future will users be advised to run sudo gedit or sudo nautilus because it is easy to advise that than explain how to set gedit or nautilus with a Polkit policy?

Nautilus is chained up because when we try to open certain system folders it refuses to do that and does not ask the user to authenticate. So, nautilus does not need a Polkit policy limiting its use because the limitations are built in. Is that true of other file managers?

Just to be clear. I do not claim credit for that script. It was put forward some time ago by someone when we (here in U+1) first noticed that gksu was not installed by default and it was pointed out that pkexec was there to be used instead.

EDIT: For reference because a little knowledge is a dangerous thing,

[http://meta.askubuntu.com/questions/6634/psa-gksu-is-no-longer-installed-by-default?cb=1](http://meta.askubuntu.com/questions/6634/psa-gksu-is-no-longer-installed-by-default?cb=1)

[http://askubuntu.com/questions/284306/why-is-gksu-no-longer-installed-by-default](http://askubuntu.com/questions/284306/why-is-gksu-no-longer-installed-by-default)

[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

That psychocats tutorial does not explain why we get those error messages but it certainly explains why we still get those error messages = developers not bothered to fix the two bugs.

Regards.

---

### Post by ventrical on 2014-05-24
Here is a counterpoint to the 'don't use sudo' argument   by Vincent Danen.

[http://www.techrepublic.com/blog/linux-and-open-source/setting-the-record-straight-on-sudo/#](http://www.techrepublic.com/blog/linux-and-open-source/setting-the-record-straight-on-sudo/#).


So there's lots of stuff, pro and con, out there.

Regards..

---

### Post by bapoumba on 2014-05-24
> **grahammechanical said:**
> 
That psychocats tutorial does not explain why we get those error messages but it certainly explains why we still get those error messages = developers not bothered to fix the two bugs.


Sorry to stir the thread off tracks here, one thing I have been wandering about but have no real answer for : would sudo -H work opening graphical apps ?
>  &#8209;H, &#8209;-set-home
    Request that the security policy set the HOME environment variable to the home directory specified by the target user's password database entry. Depending on the policy, this may be the default behavior.

---

### Post by mc4man on 2014-05-24
> **bapoumba said:**
> Sorry to stir the thread off tracks here, one thing I have been wandering about but have no real answer for : would sudo -H work opening graphical apps ?

I'd think sudo -H nautilus or gedit is still good as is 
sudo -i
nautilus or gedit
Any of those or pkexec seems better than gksudo atm.

As far as messages - 
GLib-CRITICAL **: Source ID ... seems to be an issue created with glib 2.40+, affects several apps. It's up to the app to fix so that likely precludes any fixes for nautilus or gedit.
The Gtk-WARNING **: Failed to register client:  seems to be a harmless warning, again seen with some other apps

The error: XDG_RUNTIME_DIR not set in the environment, ect. seems to come from manually creating a policy for nautilus, when the policy is installed with nautilus (nautilus-data) then it doesn't occur, "pkexec nautilus" works fine, no env is needed (which to me is better as I never run from terminal, alt+F2 or nautilus-actions via context menu.

Why that is not yet sure, if anyone wanted to see I have the start of a 14.10 proposed ppa that currently only has nautilus in it. (several additional patches inc. enabling pkexec
[https://launchpad.net/~mc3man/+archive/uptopic-props](https://launchpad.net/~mc3man/+archive/uptopic-props)
If inclined to test one can then use ppa-purge to return to repo version (nautilus-data package contains the policy so it must also be upgraded

---

### Post by bapoumba on 2014-05-25
Thanks mc4man, a good reason to get around Utopic again after I wiped it out to fresh install 14.04 and rearrange the partitions to have one free.

---

### Post by zika on 2014-05-25
> **mc4man said:**
> The error: XDG_RUNTIME_DIR not set in the environment, ect. seems to come from manually creating a policy for nautilus, when the policy is installed with nautilus (nautilus-data) then it doesn't occur, "pkexec nautilus" works fine, no env is needed (which to me is better as I never run from terminal, alt+F2 or nautilus-actions via context menu.I do beg to differ: it is not a product of any manual editing or change, simply it is not set, just try pkx I proposed above...

---

### Post by zika on 2014-05-25
> **bapoumba said:**
> would sudo -H work opening graphical apps ?Yes and that is the only proper/secure way (if anytime needed indeed) to use sudo with GUI application...

---

### Post by bapoumba on 2014-05-25
> **zika said:**
> Yes and that is the only proper/secure way (if anytime needed indeed) to use sudo with GUI application...
OK thanks :)

---

### Post by Toz on 2014-07-09
Just wanted to post working policy files for mousepad, thunar and xfce4-terminal for reference purposes.

**/usr/share/polkit-1/actions/com.ubuntu.mousepad.policy**
```

<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE policyconfig PUBLIC
 "-//freedesktop//DTD PolicyKit Policy Configuration 1.0//EN"
 "http://www.freedesktop.org/standards/PolicyKit/1.0/policyconfig.dtd">
<policyconfig>
  <vendor>mousepad</vendor>
  <vendor_url>mousepad</vendor_url>
  <icon_name>mousepad</icon_name>
  <action id="org.freedesktop.policykit.pkexec.mousepad">
   <description>Run "mousepad"</description>
   <message>Authentication is required to run Mousepad</message>
   <defaults>
     <allow_any>auth_admin</allow_any>
     <allow_inactive>auth_admin</allow_inactive>
     <allow_active>auth_admin</allow_active>
   </defaults>
     <annotate key="org.freedesktop.policykit.exec.path">/usr/bin/mousepad</annotate>
     <annotate key="org.freedesktop.policykit.exec.allow_gui">true</annotate>
   </action>  
</policyconfig>
```

**/usr/share/polkit-1/actions/com.ubuntu.thunar.policy**
```

<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE policyconfig PUBLIC
 "-//freedesktop//DTD PolicyKit Policy Configuration 1.0//EN"
 "http://www.freedesktop.org/standards/PolicyKit/1.0/policyconfig.dtd">
<policyconfig>
  <vendor>thunar</vendor>
  <vendor_url>thunar</vendor_url>
  <icon_name>thunar</icon_name>
  <action id="org.freedesktop.policykit.pkexec.thunar">
   <description>Run "thunar"</description>
   <message>Authentication is required to run Thunar</message>
   <defaults>
     <allow_any>auth_admin</allow_any>
     <allow_inactive>auth_admin</allow_inactive>
     <allow_active>auth_admin</allow_active>
   </defaults>
     <annotate key="org.freedesktop.policykit.exec.path">/usr/bin/thunar</annotate>
     <annotate key="org.freedesktop.policykit.exec.allow_gui">true</annotate>
   </action>  
</policyconfig>
```

**/usr/share/polkit-1/actions/com.ubuntu.xfce4-terminal.policy**
```

<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE policyconfig PUBLIC
 "-//freedesktop//DTD PolicyKit Policy Configuration 1.0//EN"
 "http://www.freedesktop.org/standards/PolicyKit/1.0/policyconfig.dtd">
<policyconfig>
  <vendor>xfce4-terminal</vendor>
  <vendor_url>xfce4-terminal</vendor_url>
  <icon_name>terminal</icon_name>
  <action id="org.freedesktop.policykit.pkexec.xfce4-terminal">
   <description>Run "xfce4-terminal"</description>
   <message>Authentication is required to run xfce4-terminal</message>
   <defaults>
     <allow_any>auth_admin</allow_any>
     <allow_inactive>auth_admin</allow_inactive>
     <allow_active>auth_admin</allow_active>
   </defaults>
     <annotate key="org.freedesktop.policykit.exec.path">/usr/bin/xfce4-terminal</annotate>
     <annotate key="org.freedesktop.policykit.exec.allow_gui">true</annotate>
   </action>  
</policyconfig>
```

---

### Post by rrnbtter on 2014-07-09
Greetings,
I've been using sudo since I started using linux with Karmic Koala. In that time I haven't used gksu even once so I can't say that I'm concerned that it is not here now.  Regarding this pkexec stuff, as cute as it is (and I've tried it out), I can't say that a random policy written by a random 1 out of 20 million users is any more secure than using a utility provided by the release team. I think that for myself I will continue to keep it simple and continue to use sudo.

---

### Post by sudodus on 2014-07-10
I like ***sudo*** too, but there is an investigation what to recommend for GUI programs, where plain sudo without options sometimes causes problems. The developers of Ubuntu seem to not like ***gksudo*** and to recommend ***pkexec***, and we try to understand how things work in the new versions and what to recommend for all users of Ubuntu and the Ubuntu flavours.

 *Toz* is no 'random 1 out of 20 million user', but is right now one of the investigators on behalf of the Ubuntu Forums staff. So I'm looking forward to their result.

---

### Post by rrnbtter on 2014-07-10
Greetings,
I not talking about Toz or anyone else in this thread when I say a random 1 out of 20 million users. I am saying that to have any randomly chosen  new user create a policy in Policykit  to open a graphical app seems to me to be a hazardous venture. 

After reviewing this situation I think I will start using the sudo -H as suggested by Zika. After all the only value of gksudo is to keep root from incidentally taking ownship of a file in the home dir. Given the errors produced I'm not convinced that pkexec is doing the job.

---

### Post by rrnbtter on 2014-07-10
Greetings,

> **sudodus said:**
>  The developers of Ubuntu seem to not like ***gksudo*** and to recommend ***pkexec***

A link to this information would be appreciated.

---

### Post by grahammechanical on 2014-07-10
> **rrnbtter said:**
> Greetings,



A link to this information would be appreciated.

Back during the development cycle of Trusty Tahr some of us noticed that gksu was not installed by default any more. There was a thread discussing this. In that thread someone posted links to mailing list quotes to the effect that gksu was depreciated and that when questioned about this some developers expressed surprise that users would actually want or need to edit system configuration files.

So, I guess that for the vast majority of users (those millions) the need to use pkexec is no problem because they are never going to edit system configuration files. But anyway, all this was discussed during the last cycle.

Regards.

---

### Post by sudodus on 2014-07-10
> **rrnbtter said:**
> Greetings,
I not talking about Toz or anyone else in this thread when I say a random 1 out of 20 million users. I am saying that to have any randomly chosen  new user create a policy in Policykit  to open a graphical app seems to me to be a hazardous venture. 

After reviewing this situation I think I will start using the sudo -H as suggested by Zika. After all the only value of gksudo is to keep root from incidentally taking ownship of a file in the home dir. Given the errors produced I'm not convinced that pkexec is doing the job.

Sorry for the misunderstanding,

I share your concern about this for 'any randomly chosen  new user', but think that we will soon have a satisfactory solution.

---

### Post by rrnbtter on 2014-07-10
Greetings,
@grahammechanical; Thanks! Having read a zillion of those mailings I can see how we get to here. I'm not bashing policykit, just questioning it's viability for the new crowd that Ubuntu seems to be trying to attract. Actually gksu is still installed by default, just not activated. Sudo apt-get install gksu,  and it's back, manually set. I will continue to dabble in the pkexec thing. I put it in the same box as systemd.

---

### Post by startas on 2014-07-10
A little correction : sudo for gui programs **always **causes problems, plus it trows tons of errors and warnings to the terminal. That is one of those things i dont like about linux - all this madness about security and being just a guest and not being able to login as root on your pc soon will to go to the next level - just shut down your computer, then really no one will harm it :)

---

### Post by rrnbtter on 2014-07-10
Greetings,
@sudodus; Don't think for a second that I don't respect and appreciate the effort you "old timers" have invested in this OS and Linux in general. We are just having a discussion here! As for myself I have been a avid fan of Ubuntu Unity Desktop from its inception and have used every single Dev version as my primary OS and sometimes with disasterous results. Its just a learning opportunity. No harm, no foul!

---

### Post by philinux on 2014-07-10
> **startas said:**
> A little correction : sudo for gui programs **always **causes problems, plus it trows tons of errors and warnings to the terminal. That is one of those things i dont like about linux - all this madness about security and being just a guest and not being able to login as root on your pc soon will to go to the next level - just shut down your computer, then really no one will harm it :)

The example given in this thread was :-

```
sudo **-H** guiapp
```
Only one minor gtk warning comes up when I use it for nautilus.

Look at man sudo for an explanation of the -H parameter.

---

### Post by rrnbtter on 2014-07-10
Greetings, 
I actually agree with the "spirit" of post #33. There is some satire in that thread and also some concerrn that Ubuntu is drifting toward a "run of the mill OS" that doesn't give the user any priviledges. It is possible that that can be going on as a result of the move toward phones and tablets ( a negative result) IMO.  Jeepers! My oldest son now 46 had a Red Hat (the real "red" hat on a modem) server going in the neighborhood when he was in highschool. The man page says it best. Sudo give user priviledges as decided by the owner of the system. I own my computer and I give myself full privilege. If it results in a reinstall that is my business.

---

### Post by Cavsfan on 2014-07-10
> **philinux said:**
> The example given in this thread was :-

```
sudo **-H** guiapp
```
Only one minor gtk warning comes up when I use it for nautilus.

Look at man sudo for an explanation of the -H parameter.

Here's what I got trying the above:

```
cavsfan@cavsfan-MS-7529:~$ sudo -H gedit /etc/default/grub
[sudo] password for cavsfan: 

(gedit:22629): Gtk-WARNING **: Calling Inhibit failed: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files

(gedit:22629): Gtk-WARNING **: Calling Inhibit failed: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files

```

I got the first error on making a change to the file and the second error while saving the file.

While using gksudo gedit I only got one error and did both actions as above.

```
cavsfan@cavsfan-MS-7529:~$ gksudo gedit /etc/default/grub

(gedit:25004): Gtk-WARNING **: Calling Inhibit failed: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files

```

While using pkexec (pkx is an alias for pkexec) I got the same 2 errors as sudo -H gedit

```
cavsfan@cavsfan-MS-7529:~$ pkx gedit /etc/default/grub

(gedit:30836): Gtk-WARNING **: Calling Inhibit failed: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files

(gedit:30836): Gtk-WARNING **: Calling Inhibit failed: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files
```


While using using leafpad as the text editor I received zero errors on the 3 commands:

```
cavsfan@cavsfan-MS-7529:~$ sudo -H leafpad /etc/default/grub
[sudo] password for cavsfan: 
cavsfan@cavsfan-MS-7529:~$ gksudo leafpad /etc/default/grub
cavsfan@cavsfan-MS-7529:~$ pkx leafpad /etc/default/grub
```

The last 2 opened a box to enter password, the first one asked in the terminal as you can see. 
But There were no errors whatsoever.

So I am pkexeced err I mean perplexed. :p

Why are all of the errors pointing to gedit and when leafpad is used no errors occur.
And some proof of why sudo should not be used for GUI applications [_here_]("https://help.ubuntu.com/community/RootSudo#Graphical_sudo").

---

### Post by philinux on 2014-07-10
I got no warnings (not errors) here at all with the gedit code.

I get one warning with sudo -H nautilus

---

### Post by sudodus on 2014-07-10
Which versions and flavours are you running? Are there any PPAs or other special tweaks, that might change the behaviour when elevating the permissions?

*Plural*: You and you and you ... ?

*Edit*: In Ubuntu 12.04 LTS upgraded from 8.04 LTS and 10.04 LTS running xubuntu-desktop I have no problems running gedit, leafpad, gparted with plain sudo without and option. Sloppy, I know, but it had worked hundreds of times before I learned about the complications, gksudo, sudo -i, sudo -H (and now pkexec).

---

### Post by philinux on 2014-07-10
> **sudodus said:**
> Which versions and flavours are you running? Are there any PPAs or other special tweaks, that might change the behaviour when elevating the permissions?

Plural: You and you and you ... ?

/Me is on vanilla 64 bit Ubuntu no ppa's.

---

### Post by Cavsfan on 2014-07-10
> **sudodus said:**
> Which versions and flavours are you running? Are there any PPAs or other special tweaks, that might change the behaviour when elevating the permissions?

*Plural*: You and you and you ... ?

*Edit*: In Ubuntu 12.04 LTS upgraded from 8.04 LTS and 10.04 LTS running xubuntu-desktop I have no problems running gedit, leafpad, gparted with plain sudo without and option. Sloppy, I know, but it had worked hundreds of times before I learned about the complications, gksudo, sudo -i, sudo -H (and now pkexec).

/Me I'm using plain Ubuntu in Gnome Flashback (with Compiz) on Utopic.
```
cavsfan@cavsfan-MS-7529:~$ cat /etc/*release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=14.10
DISTRIB_CODENAME=utopic
DISTRIB_DESCRIPTION="Ubuntu Utopic Unicorn (development branch)"
NAME="Ubuntu"
VERSION="14.10 (Utopic Unicorn)"
ID=ubuntu
ID_LIKE=debian
PRETTY_NAME="Ubuntu Utopic Unicorn (development branch)"
VERSION_ID="14.10"

```

I have 12.04 also as my main OS and I also have absolutely no problems or errors there using gksudo gedit either.

---

### Post by zika on 2014-07-10
> **rrnbtter said:**
> After reviewing this situation I think I will start using the sudo -H as suggested by Zika.:-D

> **startas said:**
> A little correction : sudo for gui programs **always **causes problems, plus it trows tons of errors and warnings to the terminal. That is one of those things i dont like about linux - all this madness about security and being just a guest and not being able to login as root on your pc soon will to go to the next level - just shut down your computer, then really no one will harm it :)Bolded is simply wrong with appropriate switch (as given so many times: -H):-\"
> **Cavsfan said:**
> Here's what I got trying the above:

```
cavsfan@cavsfan-MS-7529:~$ sudo -H gedit /etc/default/grub
[sudo] password for cavsfan: 

(gedit:22629): Gtk-WARNING **: Calling Inhibit failed: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files

(gedit:22629): Gtk-WARNING **: Calling Inhibit failed: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files

```

I got the first error on making a change to the file and the second error while saving the file.

While using gksudo gedit I only got one error and did both actions as above.

```
cavsfan@cavsfan-MS-7529:~$ gksudo gedit /etc/default/grub

(gedit:25004): Gtk-WARNING **: Calling Inhibit failed: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files

```

While using pkexec (pkx is an alias for pkexec) I got the same 2 errors as sudo -H gedit

```
cavsfan@cavsfan-MS-7529:~$ pkx gedit /etc/default/grub

(gedit:30836): Gtk-WARNING **: Calling Inhibit failed: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files

(gedit:30836): Gtk-WARNING **: Calling Inhibit failed: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files
```


While using using leafpad as the text editor I received zero errors on the 3 commands:

```
cavsfan@cavsfan-MS-7529:~$ sudo -H leafpad /etc/default/grub
[sudo] password for cavsfan: 
cavsfan@cavsfan-MS-7529:~$ gksudo leafpad /etc/default/grub
cavsfan@cavsfan-MS-7529:~$ pkx leafpad /etc/default/grub
```

The last 2 opened a box to enter password, the first one asked in the terminal as you can see. 
But There were no errors whatsoever.

So I am pkexeced err I mean perplexed. :p

Why are all of the errors pointing to gedit and when leafpad is used no errors occur.
And some proof of why sudo should not be used for GUI applications [here]("https://help.ubuntu.com/community/RootSudo#Graphical_sudo").You're mixing oranges and apples. Warnings from (I'll say buggy or, better, ill imbedded) editor with warnings from command(s) that provide(s) permission(s)...
The only way to get to the bottom of anything is to get to understand what is going on on as low as possible level, as with anything in life... It is even much easier today when all the documentation is available for anyone that wants to read it.

---

### Post by philinux on 2014-07-11
> **rrnbtter said:**
> After reviewing this situation I think I will start using the sudo -H as suggested by Zika.:-D

Credit to bapoumba for suggesting that in post #19 ;)

---

### Post by rrnbtter on 2014-07-11
Greetings,

> **philinux said:**
> Credit to bapoumba for suggesting that in post #19

Well! if my english doesn't fail me post #19 is a question. Post #23 is an answer and solution.:wink:
But thank you for your post bapoumba it certainly envigorated the conversation. Overall I think this has been a productive and interesting thread. A great learning opportunity. Thanks to all.

---

### Post by Elfy on 2014-07-11
Can we stop with the he said, she said , they said - anymore offtopic posts will be jailed. Thanks.

---

### Post by zika on 2014-07-11
Just to close that chapter, since my username was involved, in accordance with @Elfy, and to be quite correct, of course I did not invent the hole on the bottom of the flower-pot: manual &#8222;said that&#8220; first and it was invented by the first fathers of **sudo** and I've always emphasized that. ;)

---

### Post by Cavsfan on 2014-07-11
> **Elfy said:**
> Can we stop with the he said, she said , they said - anymore offtopic posts will be jailed. Thanks.

Can I get a definitive answer on why I get errors with gedit and not leafpad no matter if gksu or pkexec  is involved?

---

### Post by zika on 2014-07-11
With apology to **@Elfy** for obvious off-topic but I'm not the one that started it, I'm trying to help it go away... ;)
> **Cavsfan said:**
> Can I get a definitive answer on why I get errors with gedit and not leafpad no matter if gksu or pkexec is involved?Hint is hidden in [http://ubuntuforums.org/showthread.php?t=2183375](http://ubuntuforums.org/showthread.php?t=2183375) (Your thread also). As warning are saying: &#8222;The name org.gnome.SessionManager was not provided by any .service files&#8220; Going through Nautilus provided these...
You can always do a query with **qdbus**... You will get information where to look further... By doing this in CLI You do get these warning in front of You otherwise, very often, more often than You could imagine, these warnings are written to log files and You could check that by looking into them...
Definitive answer would be that gedit does/not provide/require those services and leafpad does/not... Your mileage might vary due to other service-players active at that moment.

---

### Post by Cavsfan on 2014-07-11
> **Cavsfan said:**
> Can I get a definitive answer on why I get errors with gedit and not leafpad no matter if gksu or pkexec  is involved?

> **zika said:**
> With apology to **@Elfy** for obvious off-topic but I'm not the one that started it, I'm trying to help it go away... ;)
Hint is hidden in [http://ubuntuforums.org/showthread.php?t=2183375](http://ubuntuforums.org/showthread.php?t=2183375) (Your thread also). As warning are saying: „The name org.gnome.SessionManager was not provided by any .service files“ Going through Nautilus provided these...
You can always do a query with **qdbus**... You will get information where to look further... By doing this in CLI You do get these warning in front of You otherwise, very often, more often than You could imagine, these warnings are written to log files and You could check that by looking into them...
Definitive answer would be that gedit does/not provide/require those services and leafpad does/not... Your mileage might vary due to other service-players active at that moment.

**gksudo nautilus** didn't give me any errors but, when I closed nautilus I had to press Cntl+c to get it the cursor back. I guess 6 of these and a half a dozen of the others. ;)

Edit: So, you didn't veer off-topic huh? :lolflag: Good one zika!

All I asked was a simple question and that was not answered straightforwardly. I guess it doesn't matter about these errors/warnings; or at least that is what I get out of this thread.

---

### Post by zika on 2014-07-11
> **Cavsfan said:**
> **gksudo nautilus** didn't give me any errors but, when I closed nautilus I had to press Cntl+c to get it the cursor back. I guess 6 of these and half a dozen of the others. ;)Errors or warnings?

---

### Post by Cavsfan on 2014-07-11
> **zika said:**
> Errors or warnings?

Nope none.

---

### Post by ventrical on 2014-10-24
Just thought I would bump this thread fo reminder purposes.


Regards..

---

### Post by grahammechanical on 2014-10-24
I set up pkexec to open both Gedit and Nautilus earlier on in the Utopic cycle. But when I tried it the other week those applications failed to load. I have just tried again on vivid and this is what I get

> graham@sdb8-Roll-Dev:~$ pkexec gedit
gdk_mir_display_open
Failed to connect to Mir: Failed to connect to server socket: No such file or directory


(gedit:4862): Gtk-WARNING **: cannot open display: 
graham@sdb8-Roll-Dev:~$ pkexec nautilus
gdk_mir_display_open
Failed to connect to Mir: Failed to connect to server socket: No such file or directory


(nautilus:4870): Gtk-WARNING **: cannot open display: 

"Failed to connect to MIr!" 

Now that is a surprise. And no, this is not Ubuntu Desktop Next that I am using.

Regards.

---

### Post by ventrical on 2014-10-24
> **grahammechanical said:**
> I set up pkexec to open both Gedit and Nautilus earlier on in the Utopic cycle. But when I tried it the other week those applications failed to load. I have just tried again on vivid and this is what I get


"Failed to connect to MIr!" 

Now that is a surprise. And no, this is not Ubuntu Desktop Next that I am using.

Regards.

Pkexec now installed by default!

---

### Post by ventrical on 2014-10-24
> **grahammechanical said:**
> I set up pkexec to open both Gedit and Nautilus earlier on in the Utopic cycle. But when I tried it the other week those applications failed to load. I have just tried again on vivid and this is what I get


"Failed to connect to MIr!" 

Now that is a surprise. And no, this is not Ubuntu Desktop Next that I am using.

Regards.

Yep .. thats a big surprise !

```

ventrical@ventrical-Satellite-A105:~$ pkexec --version
pkexec version 0.105
ventrical@ventrical-Satellite-A105:~$ pkexec gedit
gdk_mir_display_open
Failed to connect to Mir: Failed to connect to server socket: No such file or directory

(gedit:5752): Gtk-WARNING **: cannot open display: 
ventrical@ventrical-Satellite-A105:~$ 


```

I guess the fun really begins now . :) ehehehe

---

### Post by ventrical on 2014-10-24
gdk_mir_display_open

and so is xorg!

---

### Post by ventrical on 2014-10-24
> **grahammechanical said:**
> I set up pkexec to open both Gedit and Nautilus earlier on in the Utopic cycle. But when I tried it the other week those applications failed to load. I have just tried again on vivid and this is what I get


"Failed to connect to MIr!" 

Now that is a surprise. And no, this is not Ubuntu Desktop Next that I am using.

Regards.

btw .. those three commands we used to use to see if Mir was running no longer work, it seems. They were here:  [https://wiki.ubuntu.com/Mir/Installing#preview](https://wiki.ubuntu.com/Mir/Installing#preview)

```
ventrical@ventrical-Satellite-A105:~$ ps aux | grep unity-system-compositor 
ventric+  5911  0.0  0.1  13676  2152 pts/1    S+   11:59   0:00 grep --color=auto unity-system-compositor
ventrical@ventrical-Satellite-A105:~$ grep -i xmir /var/log/Xorg.0.log 
ventrical@ventrical-Satellite-A105:~$ ls -l /var/log/lightdm/unity-system-compositor.log 
ls: cannot access /var/log/lightdm/unity-system-compositor.log: No such file or directory
ventrical@ventrical-Satellite-A105:~$ 



```

---

### Post by ventrical on 2014-10-24
On this install 

```

unity-system-compositor
ubuntu-desktop-mir
xserver-xorg-xmir
unity8-desktop-session-mir

```

are not installed.

 So I do not understand the 
```

gdk-mir-display-open 

```
and where it is comming from.

---

### Post by Cavsfan on 2014-10-24
Why not just use leafpad and fuhgetaboutit? Leafpad has given me zero errors unlike pkexec or gedit.

---

### Post by ventrical on 2014-10-24
> **Cavsfan said:**
> Why not just use leafpad and fuhgetaboutit? Leafpad has given me zero errors unlike pkexec or gedit.

We're suppossed to be testing pkexec.

Regards..

---

### Post by zika on 2014-10-24
Short and simple:```
:~$ pkexec gedit
==== AUTHENTICATING FOR org.freedesktop.policykit.exec ===
Authentication is needed to run `/usr/bin/gedit' as the super user
Authenticating as: ****...****,,, (****...****)
Password: 
==== AUTHENTICATION COMPLETE ===
gdk_mir_display_open
Failed to connect to Mir: Failed to connect to server socket: No such file or directory
(gedit:8984): Gtk-WARNING **: cannot open display: 
:~$ pkexec env DISPLAY=$DISPLAY XAUTHORITY=$XAUTHORITY gedit
==== AUTHENTICATING FOR org.freedesktop.policykit.exec ===
Authentication is needed to run `/usr/bin/env' as the super user
Authenticating as: ****...****,,, (****...****)
Password: 
==== AUTHENTICATION COMPLETE ===
```In second case GEdit works like it is supposed to. In first it did not show up. So, nothing new at that front except that &#8222;Mir&#8220; is there, at least, as...```
:~$ dpkg -l|grep mir
ii  libmirclient8:amd64                                   0.8.0+14.10.20141010-0ubuntu1                     amd64        Display server for Ubuntu - client library
ii  libmirclient8driver-mesa:amd64                        0.8.0+14.10.20141010-0ubuntu1                     amd64        Display server for Ubuntu - client platform library for Mesa
ii  libmircommon2:amd64                                   0.8.0+14.10.20141010-0ubuntu1                     amd64        Display server for Ubuntu - shared library
```

---

### Post by Elfy on 2014-10-24
works as expected here in xubuland, at least for the policies we supply

---

### Post by Cavsfan on 2014-10-24
> **ventrical said:**
> We're suppossed to be testing pkexec.

Regards..

Oh ok guess I forgot. :)

---

### Post by ventrical on 2014-10-24
> **Cavsfan said:**
> Oh ok guess I forgot. :)

Thats ok ... I know what you are saying . Leafpad is alright!  I like it too.

regards..

---

### Post by mc4man on 2014-10-24
pkexec gedit is fine here (14.10 release upgraded to vivid
Ex. from terminal, ie. no nothing unexpected, root gedit opens as normal
> $ pkexec gedit /etc/fstab
doug@doug-Lenovo-IdeaPad-Y510P:~$

Any issues arising would be from the policy not being installed with the package, not anything to do with vivid (in regards to gedit &  policykit nothing has changed from 14.10
screen1 - auth dialog
scr. 2 typical root gedit window (w/ integrated menus as root doesn't support global

So nothing broken or changed...

---

### Post by ventrical on 2014-10-25
> **Elfy said:**
> works as expected here in xubuland, at least for the policies we supply

Absolutely no issues atm.

---

### Post by cariboo on 2014-10-25
I added 
```
pkexec synaptic
```

to /usr/share/applicaions/synaptic.desktop, as I finally got tired of typing:

```
sudo -H synaptic
```

all the time. :) it works as it should so far.

---

### Post by Elfy on 2014-10-25
I added  /usr/bin/synaptic-pkexec to Super+S as I'm lazier :)

---

### Post by cariboo on 2014-10-25
I'm not sure which one of us is lazier, one click and type password as opposed to two key presses and type password. [ATTACH=CONFIG]257452[/ATTACH] I have synaptic in my Unity launcher.

---

### Post by Elfy on 2014-10-25
draw :D

---

### Post by mc4man on 2014-10-25
single click here - 

```
sudo nano /var/lib/polkit-1/localauthority/50-local.d/package-manager.pkla
```
(redacted version below
```
[Install package synaptic]
Identity=unix-group:sudo
Action=com.ubuntu.pkexec.synaptic
ResultActive=yes
```

---

