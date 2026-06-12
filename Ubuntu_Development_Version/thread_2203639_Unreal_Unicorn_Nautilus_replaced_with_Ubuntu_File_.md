---
title: "Unreal Unicorn Nautilus replaced with Ubuntu File Manager app."
date: 2014-02-04
forum: Ubuntu Development Version
---

### Post by Cavsfan on 2014-02-04
Didn't see this anywhere.

```
    "With all the complaints and unhappyness about Nautilus upstream ripping out things like dual pane and other beloved and helpful features I expect we can do better and I think this is the right time to:

    a) collect requirements
    b) file whishlist bugs
    c) if *you* want to contribute, get in contact with the developers"

    - Oliver Grawert
```

[http://www.webupd8.org/2014/02/ubuntu-1410-might-use-converged-qml.html](http://www.webupd8.org/2014/02/ubuntu-1410-might-use-converged-qml.html)

---

### Post by QDR06VV9 on 2014-02-04
@Cavsfan I had read about this about a week ago my hopes are high on this new app.
But for now happy with Nemo:D

---

### Post by Mateusz Stachowski on 2014-02-04
All the news sites write about Ubuntu being unhappy with Nautilus but this is about using the new converged apps also on desktop. This is also about Ubuntu 14.10 not Trusty.

> Default File Manager with Unity8 in future desktops

Oliver Grawert ogra at ubuntu.com 
Thu Jan 30 17:21:44 UTC 2014


hi,


with the planned switch to unity8 in 14.10 it is most likely that we
will also start using the converged QML apps that are developed today.

[https://lists.ubuntu.com/archives/ubuntu-desktop/2014-January/004414.html](https://lists.ubuntu.com/archives/ubuntu-desktop/2014-January/004414.html)

---

### Post by grahammechanical on 2014-02-04
This File Manager is a Ubuntu Touch core app which can be installed on the desktop. You will see that it is very much a mobile app. It only accesses one partition. Which is what we would expect on a mobile device. So, there are many improvements needed if it is to replace Nautilus. It is an option. The same can be said about the Music app in Ubuntu Touch. That will import audio files from /home/music but not from another partition. And then there is Browser (Ubuntu Web Browser) which we already have. There are several Touch apps that could in the future become useful desktop applications, even default ones.

If they use less memory and less CPU resources and have similar functionality, then I am in favour of it. But expect more criticism of Ubuntu going it alone. Nothing new in that regard.

Regards.

---

### Post by Cavsfan on 2014-02-04
I guess I'm going blind! I did not notice it said 14.10; thought it said 14.04! I have a cataract in my right eye, so I'm going with one good eye here.
My bad! I thought I had stumbled onto something. :) Guess I jumped the gun. Good topic I guess though.

Thanks for the replies.

---

### Post by Elfy on 2014-02-04
we'll have a guess at the dev name for 14.10 at the same time as wondering if this will make it as well

---

### Post by Cavsfan on 2014-02-04
> **Elfy said:**
> we'll have a guess at the dev name for 14.10 at the same time as wondering if this will make it as well

Thanks Elfy! This is an interesting topic.

---

### Post by Cavsfan on 2014-02-15
Nautilus certainly leaves a lot to be desired in Trusty, at least at the present in Flashback with Compiz. There are no min. max. buttons and it oddly does not use the window decorator Emerald.
I cannot even resize Nautilus.

---

### Post by Cavsfan on 2014-02-16
> **runrickus said:**
> @Cavsfan I had read about this about a week ago my hopes are high on this new app.
But for now happy with Nemo:D

Thanks for pointing out Nemo. :D I at first thought of this guy when you mentioned it:
[ATTACH=CONFIG]250400[/ATTACH]
Since Nautilus is not what it once was here on Trusty, I installed Nemo and realized it was a nice file manager. 
Although I couldn't figure out how to make it default and was going to post that question here but I found these commands:

```
xdg-mime default nemo.desktop inode/directory application/x-gnome-saved-search
```

To check what file manager you have as default:

```
cavsfan@cavsfan-MS-7529:~$ xdg-mime query default inode/directory
nemo.desktop

```
To test it enter this in terminal:
```
xdg-open $HOME
```

That opened Nemo with my home directory and when I click on Places and then Home, Documents, etc. it opens Nemo. Sweet! :D

I got that from this page [_here_]("http://www.fandigital.com/2013/01/set-nemo-default-file-manager-ubuntu.html").

Thank you runrickus!

---

### Post by Elfy on 2014-02-16
unreal unicorn beats nemo - just saying :p

---

### Post by Cavsfan on 2014-02-16
> **Elfy said:**
> unreal unicorn beats nemo - just saying :p

:lol: Are you joshing me Elfy? I looked up unicorn in SPM and it said "Unicorn is an HTTP server for Rack applications" :p

Added: DOH! I forgot the name of this thread. :redface:

Added: Then I forgot that you named it Unreal Unicorn.  :redface:
 
I like Nemo. Does anyone know how to get it not to display on the desktop? This is what displays on the top left:

[ATTACH=CONFIG]250405[/ATTACH]

I tried in gnome tweak tools but it was already set not to display these.
I can live with it but I'd like to get that off there if possible.

---

### Post by mc4man on 2014-02-16
likely in dconf-editor - screen

---

### Post by Hazzabin on 2014-02-16
My two-pence worth, Nemo is ok-ish, my preference is Dolphin.....tho it is a shame is appears to be tied to KDE which I don't care much for.

would be great if Dolphin was completely available/suitable/workable across all Ubuntu/Linux OS'es 

I too went looking for 'unreal unicorn' can't find it anywhere either

Cavsfan, have you got 'Nemo' running in 14.04?

---

### Post by Cavsfan on 2014-02-17
> **mc4man said:**
> likely in dconf-editor - screen

Thanks for that! Fixed it perfectly! :)

[ATTACH=CONFIG]250423[/ATTACH]

> **Hazzabin said:**
> My two-pence worth, Nemo is ok-ish, my preference is Dolphin.....tho it is a shame is appears to be tied to KDE which I don't care much for.

would be great if Dolphin was completely available/suitable/workable across all Ubuntu/Linux OS'es 

I too went looking for 'unreal unicorn' can't find it anywhere either

Cavsfan, have you got 'Nemo' running in 14.04?

Yes Hazzabin I do have Nemo installed and I like it a lot better than nautilus.

Elfy got us both it looks like. :P He changed the name of the thread for me and put Unreal Unicorn in place of Trusty. Like that will be the next version of Ubuntu after Trusty. :P

---

