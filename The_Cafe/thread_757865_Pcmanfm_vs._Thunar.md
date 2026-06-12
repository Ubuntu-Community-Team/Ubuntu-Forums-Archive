---
title: "Pcmanfm vs. Thunar?"
date: 2008-04-17
forum: The Cafe
---

### Post by Pogeymanz on 2008-04-17
I am just discovering pcmanfm and it seems really awesome! I think it immediately pwned nautilus and thunar in my mind.

What do you think?



Side note: Is there a way to have pcmanfm manage the desktop, so that I can stop using Thunar?

---

### Post by misfitpierce on 2008-04-17
In my mind Nautilus is just right for me. Just works.

In a mind set of a different manager rather than Nautilus i'd prob go Thunar.

---

### Post by geoken on 2008-04-17
> **misfitpierce said:**
> In my mind Nautilus is just right for me. Just works.

 

I hate nautilus. It's on average 5x slower than Thunar and I can't really see any features that it has and Thunar doesn't. I could deal with the slowness if it had some redeeming qualities, but I fail to see any killer feature present in Nautilus which Thunar lacks.

My dream would be a 1:1 GTK clone of Dolphin.

---

### Post by billlang675 on 2008-04-17
Nautilus or mc in a terminal are OK with me.:)

---

### Post by SunnyRabbiera on 2008-04-17
I like Pcmanfm, its a really cool compared to thunar and Nautilus...
if it only had file type saving support and trashcan support.

---

### Post by LaRoza on 2008-04-17
I haven't use it. I will now.

I use Thunar and mc.

---

### Post by sisco311 on 2008-04-17
> **EmosSuck777 said:**
> 
Side note: Is there a way to have pcmanfm manage the desktop, so that I can stop using Thunar?

```
gksu mousepad /etc/xdg/xfce4-session/xfce4-session.rc
```Change:
*Client2_Command=Thunar,--daemon*
to
*Client2_Command=pcmanfm,--daemon*

---

### Post by OoooMatron on 2008-04-17
Does those other two support smb , ssh and ftp connections? Otherwise they are both useless to me.

---

### Post by Seisen on 2008-04-17
Between the two of them Pcmanfm but personally I like mc.

---

### Post by geoken on 2008-04-17
> **OoooMatron said:**
> Does those other two support smb , ssh and ftp connections? Otherwise they are both useless to me.

When you say SMB, do you mean being able to browse a share you already mounted or do you mean network discovery?

---

### Post by herbster on 2008-04-17
Since I set up all my network shares myself in my fstab, thunar rocks. It's blazing fast, and the thunar-thumbnailer, thunar-archive-plugin and thunar-media-tags-plugin really kick butt. The thumbnailer is lightning fast.

---

### Post by bigbrovar on 2008-04-17
for me the coolest thing about pcmanfm is that it can open directories in tabs that is something neither nautilus and thunar has ... beside it is blazingly fast .. the downside is the lack of trash support .. but in all i prefer it to nautilus ..although i still use nautilus cus i dont know how to make pcman default in gnome.. and if doing so wont break ubuntu .. :(

---

### Post by Pogeymanz on 2008-04-17
> **SunnyRabbiera said:**
> I like Pcmanfm, its a really cool compared to thunar and Nautilus...
if it only had file type saving support and trashcan support.

Could you elaborate on the "file type saving support" thing? I'm just not understanding what you are talking about.

---

### Post by pt123 on 2008-04-17
Thunar is so limited doesn't support samba shares, there is not Find tool.

---

### Post by Kingsley on 2008-04-17
> **pt123 said:**
> Thunar is so limited doesn't support samba shares, there is not Find tool.

I'm pretty sure pcmanfm doesn't support samba shares either, and I'm not sure about the latter. 

My preference is Nautilus.

---

### Post by swoll1980 on 2008-04-17
> **geoken said:**
>  I can't really see any features that it has and Thunar doesn't. .

Network browser for one that I know of. You can use pyneighborhood 
. Once you get away from nautilus theres all these things you start to notice that are missing

---

### Post by wersdaluv on 2008-04-17
I go for PCManFM. Maybe, simple because of the tabbed browsing feature, which is very very important.

---

### Post by atomkarinca on 2008-04-17
> **pt123 said:**
> Thunar is so limited doesn't support samba shares, there is not Find tool.

With a little trick, it can. [Here]("http://polishlinux.org/apps/window-managers/catfish-easily-find-stuff-in-thunar/")'s the trick.

---

### Post by cardinals_fan on 2008-04-17
I love Thunar :)

---

### Post by SunnyRabbiera on 2008-04-18
> **EmosSuck777 said:**
> Could you elaborate on the "file type saving support" thing? I'm just not understanding what you are talking about.

meaning on both nautilus and konqueror it has a document creator on the fly, PCmanFM however can only create text files and new folders

---

### Post by Kiri on 2008-04-18
How can I install pcmanFM?

When I run the ./configure I get this error:

```
checking for SN... configure: error: Package requirements (libstartup-notification-1.0) were not met:

No package 'libstartup-notification-1.0' found

```

---

### Post by gn2 on 2008-04-18
I have never tried Pcmanfm for one reason, Thunar works perfectly for my needs.

---

### Post by graabein on 2008-04-18
I use PCManFM on both GNOME and Xfce. I don't have any need for SMB, SSH or FTP. Have not looked into desktop search either. It's fast and has tabs so it fits my needs.

---

### Post by geoken on 2008-04-18
> **swoll1980 said:**
> Network browser for one that I know of. You can use pyneighborhood 
. Once you get away from nautilus theres all these things you start to notice that are missing

I never noticed because network discovery through nautilus is totally broken for me so I have to use pyNeighborhood anyway. Even if they fixed it, it would be a non-issue for me because I would still use Thunar for network transfers because Nautilus frequently crashes half-way through.

---

### Post by Tomatz on 2008-04-18
Just installed it:

Its ok but its no where near as good as nautilus or thunar. With the nautilus scrips and all, nautilus IMO is much more powerfull.

Also on my hardware i noticed no difference in performance but on older hardware this would probably not be the case.

Its not for me.

---

### Post by Kiri on 2008-04-18
Just tried out KDE, and I have to say Dolphin (KDE default file manager) is a much nicer file manager than any of the others I have tried in gnome including nautilus, pcman, etc. 

It has dual pane split view which I think is really essential for a good file manager, and handy functions like open terminal etc, basically it just seemed much more intuitive and clean to use. 

Unfortunately running it in gnome it is not so nice :(

---

### Post by Seisen on 2008-04-18
> **Kiri said:**
> How can I install pcmanFM?

When I run the ./configure I get this error:

```
checking for SN... configure: error: Package requirements (libstartup-notification-1.0) were not met:

No package 'libstartup-notification-1.0' found

```

Pcmanfm is available in the repos starting with 7.04

---

### Post by Kiri on 2008-04-18
thanks seisen. 
The one in the repos seems to be an older version, but I found a relatively new deb here:
[http://www.getdeb.net/release.php?id=2374]("http://www.getdeb.net/release.php?id=2374")

---

### Post by ice60 on 2008-04-18
i've never really used Pcmanfm because it always crashes on my suse install. i love Thunar though, i've added lots of extra right-click actions, can Pcmanfm do that too?

here are some of the extra options i've added to Thunar 8)

[[IMG]http://img501.imageshack.us/img501/1274/thunar0ft6.th.png[/IMG]](http://img501.imageshack.us/my.php?image=thunar0ft6.png)

[[IMG]http://img397.imageshack.us/img397/2807/thunar1jb6.th.png[/IMG]](http://img397.imageshack.us/my.php?image=thunar1jb6.png)

---

### Post by geoken on 2008-04-18
> **Kiri said:**
> Just tried out KDE, and I have to say Dolphin (KDE default file manager) is a much nicer file manager than any of the others I have tried in gnome including nautilus, pcman, etc. 

It has dual pane split view which I think is really essential for a good file manager, and handy functions like open terminal etc, basically it just seemed much more intuitive and clean to use. 

Unfortunately running it in gnome it is not so nice :(

It also has the 'show in groups' view which I love. It makes browsing large directories so much easier because it gives a strong visual cue to differentiate the files based on your sort criteria. For example, if you sort by name you can scroll through the directory super fast yet still easily tell when you've scrolled to the right point.

[IMG]http://enzosworld.gmxhome.de/images/view_mode_2.png[/IMG]

---

### Post by dashnak on 2008-04-18
I love PCManFM, I use it by default, in both GNOME and openbox.

---

### Post by capink on 2008-04-18
I would use pcmanfm if it has an alternative for thunar's custom actions. Maybe it will be added in the future. In the mean time I will stick to thunar.

---

### Post by Onyros on 2008-04-18
PCManFM has been my default for some time now :)

---

### Post by will1911a1 on 2008-04-18
I run Thunar on my Arch install.  It does exactly what I want so I don't feel the need to use anything else.

---

### Post by SnakeHips on 2008-04-18
I was surprised to find that Thunar had no "file search" tool at default ,unless i'm missing something...anyhow i had a look around and found this 
[http://thunar.xfce.org/pwiki/documentation/custom_actions](http://thunar.xfce.org/pwiki/documentation/custom_actions)
which has some examples.... and suggest's using the gnome-search-tool in gnome-utils
[http://thunar.xfce.org/pwiki/documentation/custom_actions#examples](http://thunar.xfce.org/pwiki/documentation/custom_actions#examples)

Have i missed something and/or what alternatives for file search do you use in Thunar?

---

### Post by will1911a1 on 2008-04-18
> **SnakeHips said:**
> I was surprised to find that Thunar had no "file search" tool at default ,unless i'm missing something...anyhow i had a look around and found this 
[http://thunar.xfce.org/pwiki/documentation/custom_actions](http://thunar.xfce.org/pwiki/documentation/custom_actions)
which has some examples.... and suggest's using the gnome-search-tool in gnome-utils
[http://thunar.xfce.org/pwiki/documentation/custom_actions#examples](http://thunar.xfce.org/pwiki/documentation/custom_actions#examples)

Have i missed something and/or what alternatives for file search do you use in Thunar?

If I need to hunt down a file I usually just use the command line.

---

### Post by SnakeHips on 2008-04-18
> **will1911a1 said:**
> If I need to hunt down a file I usually just use the command line.

same here.......but some times i just need to work from a GUI.....and i cant at the moment :lolflag:

---

### Post by ice60 on 2008-04-18
> **SnakeHips said:**
> I was surprised to find that Thunar had no "file search" tool at default ,unless i'm missing something...anyhow i had a look around and found this 
[http://thunar.xfce.org/pwiki/documentation/custom_actions](http://thunar.xfce.org/pwiki/documentation/custom_actions)
which has some examples.... and suggest's using the gnome-search-tool in gnome-utils
[http://thunar.xfce.org/pwiki/documentation/custom_actions#examples](http://thunar.xfce.org/pwiki/documentation/custom_actions#examples)

Have i missed something and/or what alternatives for file search do you use in Thunar?
i think you missed this post
[http://ubuntuforums.org/showpost.php?p=4738255&postcount=18](http://ubuntuforums.org/showpost.php?p=4738255&postcount=18)

there's an old thread here about adding both searches to thunar. i think this is it -
[http://ubuntuforums.org/showthread.php?t=214059](http://ubuntuforums.org/showthread.php?t=214059)

---

### Post by herbster on 2008-04-18
> **ice60 said:**
> i've never really used Pcmanfm because it always crashes on my suse install. i love Thunar though, i've added lots of extra right-click actions, can Pcmanfm do that too?

here are some of the extra options i've added to Thunar 8)

[[IMG]http://img501.imageshack.us/img501/1274/thunar0ft6.th.png[/IMG]](http://img501.imageshack.us/my.php?image=thunar0ft6.png)

[[IMG]http://img397.imageshack.us/img397/2807/thunar1jb6.th.png[/IMG]](http://img397.imageshack.us/my.php?image=thunar1jb6.png)

Just curious if you are aware that there's a thunar-archive-plugin, one really doesn't need the Custom Actions for extraction/archiving (though of course if you prefer).

---

### Post by SnakeHips on 2008-04-18
> **ice60 said:**
> i think you missed this post
[http://ubuntuforums.org/showpost.php?p=4738255&postcount=18](http://ubuntuforums.org/showpost.php?p=4738255&postcount=18)

there's an old thread here about adding both searches to thunar. i think this is it -
[http://ubuntuforums.org/showthread.php?t=214059](http://ubuntuforums.org/showthread.php?t=214059)

Thanks .i'd seen the "catfish" post but missed the other. I'm having a look at it right now.

---

### Post by ice60 on 2008-04-18
> **herbster said:**
> Just curious if you are aware that there's a thunar-archive-plugin, one really doesn't need the Custom Actions for extraction/archiving (though of course if you prefer).
i broke the thunar-archive-plugin at one point, or used a version of thunar that didn't support it and made them then. i think it was when i upgraded thunar, or was using a beta. it works now though.

---

### Post by Jammy4041 on 2008-04-18
I would prefer Thunar when I install Xubuntu. However, I did download and install PCManfm and to be honest, I don't like it. (In Ubuntu at least, that is.)

However, Nautilus in my opinion is better. I can not comment on Dolphin/ Konqueror. Never used Kubuntu.

---

### Post by Pogeymanz on 2008-04-25
Do you think Thunar will ever have ssh support? I am just now discovering this and it's pretty awesome, but nautilus is way too slow for my normal use. I might keep it installed just for ssh browsing.

---

### Post by Weevil on 2008-10-14
> **Pogeymanz said:**
> Could you elaborate on the "file type saving support" thing? I'm just not understanding what you are talking about.

It's supported by now... but pcmanfm from the repositories is an old version that doesn't have the ability :(


From [http://pcmanfm.sourceforge.net/screenshots.html](http://pcmanfm.sourceforge.net/screenshots.html)


[IMG]http://pcmanfm.sourceforge.net/screenshot4.png[/IMG]

---

### Post by Weevil on 2008-10-14
Well... just installed the latest stable pcmanfm (0.5) from source and it doesn't support setting default actions for (unknown) file types... Guess I got fooled!

---

### Post by LtPitt on 2010-01-29
Hi All!

Just my two cents:

I'm using a wonderful old powerbook g3 300mhz 128mb ram and it was close to useless because os x is REALLY slugghish and for os 9 it's really DAMN hard to find applications now (mainly a serious web browser... Classilla is on his way but I just have to play, you know? :D).
Then I popped in a LOT of linux distros.

It took me AGES, believe me.

Any install took hours and lots of problems.
My final solution was:

xubuntu-alternative-ppc.iso install...

and

sudo apt-get install xorg gdm lxde


So I got the chance to "meet" pcmanfm.
Now I got a fast and working little laptop with firefox 3.5, filezilla, pidgin, abiword, gnumeric and a lot more :D

Ok, since I'm done with sharing happiness I can get to the point:
Thunar was terrible in my really low end mac.
Slow, slow and slow again.

Pcmanfm has no trash support, ok...
Not great handling of "new file" and similar stuff...
Not great handling of assigning custom icons but...
It's really fast.
And it really works :)

---

### Post by chucky chuckaluck on 2010-01-29
i had a bad experience with the way deletions were handled in an early version of pcmanfm and never really gave it a second chance. i've used thunar probably the most of any fm and always like the custom actions (i thought it was sad that i had more customized ways to do wallpapers using thunar in openbox, with feh, than in xfce). and, whenever i use kde, i love dolphin. but, just as leafpad eventually lost me to nano, gui fms have lost out to mc.

---

### Post by Grifulkin on 2010-01-29
I use pcmanfm, on all of my systems I don't need it to really do much, the occasional file lookup when I'm too lazy to use the terminal.  Also I have used Rox which is very minimal it's nice but I don't think it was for me.  But yeah nautilus=gnome dependencies, no thanks.

---

### Post by croote on 2010-10-28
Hi,

I've just discovered pcmanfm**2** from this thread :
[http://ubuntuforums.org/showpost.php?p=9781426&postcount=85](http://ubuntuforums.org/showpost.php?p=9781426&postcount=85)

Everything I need seems to be pack in: "extract here" option in the mouse left menu, tabs, autoselection of "Yes" in the delete confirm dialog, trash support etc.

Very nice, really!
And still very fast ;-)

---

### Post by Spice Weasel on 2010-10-28
Thunar seems to be a lot smoother over here, and it doesn't have any more dependancies than PCManFM. So that's what I use.

---

### Post by ufugu on 2010-10-28
I love Thunar the best (the renamer is AWESOME) but it really, really needs tabs.  So helpful in a file manager.

---

### Post by lykeion on 2010-10-28
> **croote said:**
> Hi,

I've just discovered pcmanfm**2** from this thread :
[http://ubuntuforums.org/showpost.php?p=9781426&postcount=85](http://ubuntuforums.org/showpost.php?p=9781426&postcount=85)

Everything I need seems to be pack in: "extract here" option in the mouse left menu, tabs, autoselection of "Yes" in the delete confirm dialog, trash support etc.

Very nice, really!
And still very fast ;-)

Thanks a lot. Now I also discovered pcmanfm2. It seems as fast as original with added extra features. Really good.

---

