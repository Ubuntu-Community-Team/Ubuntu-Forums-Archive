---
title: "Very new to servers"
date: 2009-02-27
forum: Server Platforms
---

### Post by ForMar on 2009-02-27
so I am getting ready to put together a server computer but unfortunately I have very high expectations of what I want to do with it one in particular:  

           I want it to have the full functionality of a server, (firewall dns, nfs, etc...) but also I want to be able to play videos from the server to a tv connected to it. Is there any combo of some window environment  and a program I can use?  When it comes to the environment though I dont want some full blown desktop that once started will never go away, something that I can bring up and down as needed would be great! 

Plz tell me if this just is not possible to combine these two features 


Thanks for your time and help!

---

### Post by Iowan on 2009-02-27
Dunno about playing videos, but it IS possible to install a window manager on a server.  There are a few threads posing similar questions.  I'll see if I can find a few links - or you can search for a few yourself.

---

### Post by ForMar on 2009-02-27
> **Iowan said:**
> Dunno about playing videos, but it IS possible to install a window manager on a server.  There are a few threads posing similar questions.  I'll see if I can find a few links - or you can search for a few yourself.

I look around alot before I made this post and it is possible to put a window environment on the server but then I'm stuck with it. I'm looking for something that can be turned on and off without having to reboot so I can run something like myth from one server computer

---

### Post by hictio on 2009-02-27
> **ForMar said:**
> I look around alot before I made this post and it is possible to put a window environment on the server but then I'm stuck with it. I'm looking for something that can be turned on and off without having to reboot so I can run something like myth from one server computer

You can easily install a Window Manager (hell even a full blown Desktop Environment) to your Ubuntu Server box.
Of course, a minimal Window Manager will be leaner and faster *and* since this is a server, it'll have less components, therefore, less update time, and less possibilities of security bugs.

Check this links: 
. [Install on Low Memory Systems](https://help.ubuntu.com/community/Installation/LowMemorySystems)
. [Ubuntu Minimal Desktop](http://wiki.dennyhalim.com/ubuntu-minimal-desktop)

The other question, you don't need to reboot to enable/ disable the graphical environment; be that a Window Manager or a full whistle Desktop Environment.

If you have already a Desktop Environment enabled, and you are already booting to a graphical login, and want to disable it momentarily, check [here](http://ubuntu-virginia.ubuntuforums.org/showpost.php?p=6412706&postcount=9).

If you want to disable the graphical environment for good, type:

```

sudo /etc/init.d/gdm stop ENTER

```

To re-enable, go for:
```

sudo /etc/init.d/gdm start ENTER

```

---

### Post by ForMar on 2009-02-27
Sweet thanks alot I'm sure you guys will hear alot from as I try to get this machine running :P

---

### Post by R.Bucky on 2009-02-28
As far as the window manager is concerned... I have an Ubuntu Server box that has mozilla and gedit installed. I ssh into the server and type in firefox. Although my server has no window manager or GUI installed, firefox works with the graphics on my regular web browsing box instead of my server. Also works with gedit - I hate vi! Otherwise, you might want to try using vlc. It has great streaming capabilities from remote servers and such.

---

### Post by linux_tech on 2009-03-01
Here is a good server reference
[https://help.ubuntu.com/8.04/serverguide/C/index.html](https://help.ubuntu.com/8.04/serverguide/C/index.html)

---

### Post by bigbearomaha on 2009-03-01
Depending on the format and nature of the video files you are wanting to run, you don't need a wm or de.

if they are simply mp4 or avi files, then you can use NFS or samba to share the dir that holds them and connect to that from a machine that will play them.

If you are talking about streaming video, which is over rated in my own opinion, but a lot of folks do it, then you might have an easier time in a gui environment with set up, but  then simply telinit to a non x runlevel when config is done.

have fun, learn lots,

Big Bear

---

### Post by dereknashvilleff on 2009-03-10
> **R.Bucky said:**
> As far as the window manager is concerned... I have an Ubuntu Server box that has mozilla and gedit installed. I ssh into the server and type in firefox. Although my server has no window manager or GUI installed, firefox works with the graphics on my regular web browsing box instead of my server. Also works with gedit - I hate vi! Otherwise, you might want to try using vlc. It has great streaming capabilities from remote servers and such.
i noticed you said you weere able to ssh and run firefox. I have both those installed on mine as i started with a full desktop to get it set up "noob, they all mutter to them selves". But, my question is, can i ssh and run graphics from a windows machine? If so how. I know it is called x forwarding or something but i don't understand how to do it. Thanks.

---

### Post by hyper_ch on 2009-03-10
> **dereknashvilleff said:**
> I know it is called x forwarding or something but i don't understand how to do it. Thanks.

you need to enable it.

---

### Post by dereknashvilleff on 2009-03-10
Thanks for the reply i assumed it was something like that. Sincce i last posted i have learned how to ssh remotely but am having trouble with the vnc tunnelling thing. I am pretty close to doing this xforwearding, i just need someone to point me in the right direction. i.e. how does one enable it? Just check enable x forwarding and poof it works? dont understand.

---

### Post by hyper_ch on 2009-03-10
vnc and x-forwarding are two different things.

with vnc you will have a desktop displayed that the other one would also see.

with x-forwarding you just forward "graphical" applications from the server to your computer without being required to run a full-fledged gui on the server.

---

### Post by dereknashvilleff on 2009-03-11
> **hyper_ch said:**
> vnc and x-forwarding are two different things.

with vnc you will have a desktop displayed that the other one would also see.

with x-forwarding you just forward "graphical" applications from the server to your computer without being required to run a full-fledged gui on the server.
ih, that makes sense,  ok now i know what to look for i will get that done. Thanks so much.

---

