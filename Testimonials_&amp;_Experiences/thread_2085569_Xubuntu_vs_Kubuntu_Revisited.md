---
title: "Xubuntu vs Kubuntu Revisited"
date: 2012-11-18
forum: Testimonials &amp; Experiences
---

### Post by llanitedave on 2012-11-18
About [3 weeks ago]("http://ubuntuforums.org/showthread.php?t=2077030") I posted regarding using both Kubuntu and Xubuntu in daily work, and came to the conclusion that Kubuntu was a slightly better choice for me.

Now I'm leaning the other way.  I've fixed Xubuntu's double-display of volumes, and the window frames and behaviors are simple, attractive, intuitive and fast.  I find I'm more productive in Xfce.

KDE is tweakable to the nth degree, and I enjoy playing with it -- for a while.  But it's just not as stable.  The Wallet has gone crazy recently, and I had to disable it, as it was preventing me from easily connecting to different wireless signals.  Changing the GTK window appearance in the System Settings is problematic, and its not finding the themes or fonts I installed.  Geany crashes regularly in KDE, and is often reluctant to actually run an application I'm working on.
And a wxPython app I've been developing inexplicably stopped displaying its menu bar in KDE, while in both Xubuntu and Windows it displays flawlessly.

Xubuntu is pretty much set it and forget it -- and it feels faster too.

Thing is, I still prefer a lot of the individual KDE apps, such as Amarok for one, but they actually look and behave just as good on Xubuntu as they do in KDE, while I can't really say the same about GTK+ apps running in Kubuntu.

I like the eye candy in KDE, but it's becoming too much of a hassle to keep it.

Now, if only the Xfce folks would get rid of that rat...

---

### Post by lancest on 2012-11-18
Went with Ku 12.10 for about a month.
Beautiful system, overly complex IMHO. 

Xubuntu 12.10 - kept losing autohide panel settings for instance, keyboard functionality missing, Bluetooth issues. 

(Xubuntu 12.04 might be the best choice actually who knows)

Back to Ubuntu 12.10.

Unity's keyboard centric approach is key for me. 
Forgot my mouse the other day and understood better.

---

### Post by pqwoerituytrueiwoq on 2012-11-18
i think it is a mouse

 you can get compiz working in xfce
```
sudo sed -i "s/    xfce4-session/    Compiz \&\n    xfce4-session/" /etc/xdg/xfce4/xinitrc 
```don't forget to make this scrip executable (*sudo chmod +x /usr/local/bin/Compiz*)```
~$ cat /usr/local/bin/Compiz 
#!/bin/bash
if [ ! -f ~/.compiz ];then
    exit
fi
echo "-------------New-Session-------------" > /tmp/compizLog
x=0;
if [ 0`pidof compiz` -eq 0 ];then
    while [ 0`pidof xfwm4` -eq 0 ];do
        if [ $x -gt 300 ];then
            break
        fi
        sleep 0.02
        x=$(($x+1))
        echo "I know you are going to start xfwm4..." >> /tmp/compizLog
    done
else
    echo "----Compiz was already running!----" >> /tmp/compizLog
fi
compiz --replace >> /tmp/compizLog
state="$?"
echo "Compiz exited status code: $state" >> /tmp/compizLog
while [[ ! $state -eq 0 || -z "$first" ]];do
    sleep 2
    if [ $state -eq 0 ];then
        echo "---------Crash--Assumed------------" >> /tmp/compizLog
    else
        echo "---------Crash-Detected------------" >> /tmp/compizLog
    fi
    compiz --replace >> /tmp/compizLog
    state="$?"
    first="$state"
    echo "Compiz exited status code: $state" >> /tmp/compizLog
done
echo "-------------End-Session-------------" >> /tmp/compizLog
if [ 0`pidof compiz``pidof xfwm4` -eq 0 ];then
    xfwm4 --daemon
fi
exit
```now if you have a file called .compiz in your home folder compiz will autostart
this way your guest does not have compiz
```
touch ~/.compiz
```you should make a script to remove /tmp/compizLog at logout, it will break account switching if you don't
```
~$ cat /etc/lightdm/lightdm.conf 
[SeatDefaults]
greeter-session=lightdm-gtk-greeter
user-session=xubuntu
session-cleanup-script=rm /tmp/compizLog
```

---

### Post by Tamlynmac on 2012-11-18
> llanitedave

Since this isn't a help section, I won't comment on any support issues which could result in thread closure.

I agree with your Xubuntu assessment  and hope you continue enjoying the release. Thank you for sharing your feedback.

Good Luck

---

### Post by mastablasta on 2012-11-19
haven't had any gtk+ issues in KDE.
 
Xubuntu has keyring, KDE has wallet. so far it is working. we will see later when i manage to install it to notebook.
 
Geany? something wrong with native Kdevelop?

---

### Post by llanitedave on 2012-11-19
I understand this isn't a support thread, so I'm not asking for solutions.  I'm still exploring and gradually figuring things out as I go.

I do wonder how many of my issues are hardware-related.  Most of them occur on my laptop, which is a Toshiba Satellite P775 with the Nvidia Optimus graphics card.  I know there have been a lot of issues with this card, and for this reason I'm a bit worried about adding things like Compiz that might trigger something.

At home I have a self-built desktop, that has none of these problems. My only problem is that I'm not home often enough to take full advantage of it.  My work keeps me away and on the laptop.

Well, I partially take it back.  I did have one big problem with the desktop.  When I tried to do a live upgrade in Unity from 12.04 to 12.10 it hosed everything. That's why I shifted back to the Xubuntu/Kubuntu duo in the first place, and that's why I'm reluctant to try Unity again.  I'm pretty sure that if I did a re-install rather than an upgrade it would work better, but at this point I simply don't feel the motivation to risk it any more.  I'm currently content with the two versions that I have.

---

### Post by llanitedave on 2012-11-19
> **mastablasta said:**
> 
Geany? something wrong with native Kdevelop?

I haven't actually looked at Kdevelop in a long time, although I've heard good stuff about it.

The application I'm working on will be primarily used in Windows, and I've been switching between Eclipse when I'm working in Windows and Geany when I'm in Linux.

I tried Eclipse in Linux, but just getting things configured was a time-consuming nightmare.  It went a lot more smoothly on Windows.

Geany is nice, simple, fast, and until very recently, completely reliable. (and still is on Xubuntu).

I'm not wedded to any particular IDE, though, and I'm open to trying several.  I recently downloaded Spyder, and I'll be looking at that one when I have time, probably after I'm done with the beta version of my current project.

I'm willing to be convinced to try KDevelop, or QTDevelop, or any other that might suffice.

---

### Post by mastablasta on 2012-11-19
well i haven't tried KDE based ones as well. since i am not really a developer, though i may need to learn a thing or two in the future. i think i used geany once (in Xubuntu) to find and change something. it's a nice IDE.
 
anyway i prefer to have same or similar looking applications in windows and in linux. luckilly there is KDE for windows project and you get a nice package manager and you can use KDE apps also in windows. there are 2 downsides - 1 i think the packages are not always up to date, 2 - it will pull about 350MB dependencies down when you first install a KDE programme. 
 
i have skrooge and quassel installed in windows. maybe soon more will join.

---

### Post by whatthefunk on 2012-11-19
> **llanitedave said:**
>  The Wallet has gone crazy recently, and I had to disable it, as it was preventing me from easily connecting to different wireless signals.

I love KDE like crazy, its been my sole DE for over a year now, but I ***_[COLOR="Red"]HATE[/COLOR]_***, absolutely ***_[COLOR="Red"][SIZE="3"]HATE[/SIZE][/COLOR]_*** KDE Wallet.  My hate for this program is on the same level as my hate for Hitler, Stalin, and Korean pop music.  KDE developers really need to do something about this malignant abomination.

---

### Post by Y^2om&amp;#7sgP on 2012-11-19
Used KDE for a while a few years and liked it, but after an update, usb sticks and cd's refused to muont.

Gave up and went back to Ubuntu with gnome, but then came Unity...I guess I'm one of those who hate it with a a passion, so tried Xubuntu.

Love XFCE, fast, responsive, and can do everything I need.

May have to try Kubuntu and give KDE another go :)

---

### Post by LanceHaverkamp on 2012-11-19
KDE is a cruise ship: big, pretty, lots to do & see, though usually slow, and consumes lots of resources.

XFCE is a small yacht: lightweight, quick, efficient, and has enough gadgets to still be entertaining.

Gnome is currently a shipwreck, but that will get fixed.

LXDE is a one-person catamaran: Fast and small, but not enough comfort or gadgets for end-users.

---

### Post by Peripheral Visionary on 2012-11-19
There's no [COLOR=Magenta]**"Like"**[/COLOR] button or I'd sure use it for your description, Lance!

---

### Post by QIII on 2012-11-19
KXGLbuntu?

---

### Post by llanitedave on 2012-11-19
> **whatthefunk said:**
> I love KDE like crazy, its been my sole DE for over a year now, but I ***_[COLOR="Red"]HATE[/COLOR]_***, absolutely ***_[COLOR="Red"][SIZE="3"]HATE[/SIZE][/COLOR]_*** KDE Wallet.  My hate for this program is on the same level as my hate for Hitler, Stalin, and Korean pop music.  KDE developers really need to do something about this malignant abomination.

=D>

I can see a use for it, the concept isn't bad. But its market is for super-power users that have loads of hard-to-remember passwords.  Most people have just a few that they remember easily.  The wallet should be simplified and made an opt-in, not a default tyrant on your desktop.

Someone mentioned the Xfce keyring earlier -- I don't even know it's there, unless I actually want it.

A security feature that causes so much annoyance that you end up turning it off doesn't enhance your security.

---

### Post by mastablasta on 2012-11-20
> **LanceHaverkamp said:**
> KDE is a cruise ship: big, pretty, lots to do & see, though usually slow, and consumes lots of resources.
 .
 
except that Gnome is currently using more resources than KDE. in kde you can use 180-200MB for example. i haven't seen it use CPU intensivelly (the desktop itself i mean). so i am not sure what resources are being used. i am curious though as i plan to install it on netbook. if it really does use too many resources than XUbuntu might be more suitable.
 
however i haven't seen this personally.
 
KDE has netbook interface and also tablet is under development. i doubt it would work so well on tablet if it used excessive resources.

---

### Post by Linuxisfast on 2012-11-20
I tried both as well but found Unity to be the most functional and useful especially with the side panel and app indicators. KDE Kubuntu is superb and quicker than Unity with latest KDE 4.93 but samba sharing is a pain and not as efortless as in Unity. Xubuntu was snappy but I kept getting crash errors. I tried the x32 and x64 flavors of 12.01LTS and 12.10. So back to Unity for good.

---

### Post by Erik1984 on 2012-11-20
> **llanitedave said:**
> =D>

I can see a use for it, the concept isn't bad. But its market is for super-power users that have loads of hard-to-remember passwords.  Most people have just a few that they remember easily.  The wallet should be simplified and made an opt-in, not a default tyrant on your desktop.

Someone mentioned the Xfce keyring earlier -- I don't even know it's there, unless I actually want it.

A security feature that causes so much annoyance that you end up turning it off doesn't enhance your security.

*All people* should use hard-to-remember, long passwords :P Problem is that I don't want to store them all in Kwallet as I already have them in KeePassX. Unlike KPX, Kwallet is not so portable to other operating systems / desktop environments.

---

### Post by llanitedave on 2012-11-21
> **Euroman said:**
> *All people* should use hard-to-remember, long passwords :P Problem is that I don't want to store them all in Kwallet as I already have them in KeePassX. Unlike KPX, Kwallet is not so portable to other operating systems / desktop environments.

Long passwords I agree with, but I'm too old to remember anything hard to remember.  I use a phrase that means something to me, but no one else.

The biggest problem is that the more keys you have to tap, the higher your chences of a typo, and since my fingers as often as not don't go where I tell them to, long passwords past a certain point can make it impossible for me to log on.

---

### Post by mastablasta on 2012-11-22
> **Linuxisfast said:**
> IKDE Kubuntu is superb and quicker than Unity with latest KDE 4.93 but samba sharing is a pain and not as efortless as in Unity. .
 
haven't tried KDE 4.93 yet, however in the one that ships with 12.04 it's right click on folder >properties>sharing and then tick enable in share with samba box.

---

### Post by Elfy on 2012-11-22
> This is not the place for full-scale debate or vigorous discussion, but feedback to the original poster is welcome.

Closed

---

