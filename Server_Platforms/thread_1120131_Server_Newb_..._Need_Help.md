---
title: "Server Newb ... Need Help"
date: 2009-04-08
forum: Server Platforms
---

### Post by norman_069 on 2009-04-08
Hello,  If this is not the right place for this then please let me know.

I have a few questions on servers and would appreciate all the input i can get. My goal is to have a Server set up at home that i can access any where there is an internet connection.  The server will be used as storage as well as running programs installed on the server from my laptop.  

First of all i am a newb to servers but not to ubuntu.  Being a newb should i go with windows server 2003 or ubuntu server. I currently have a laptop that is dual booted and a desktop that is dual booted with windows xp and ubuntu 8.10. I want to only use ubuntu but because of my school and work i need certain windows programs.

Will the laptop of one operating system be able to use all the functions of a server from the opposite operating system?

Should i Have two servers one with windows and one with ubuntu, that are connected together so i can access either one when i want?  And is this even possible.?

Last (well at least for now) is it possible to set up a ubuntu server that is connected to a desktop computer running windows and be able to run programs off of that desktop through the server on my laptop.

Thanks for all the help and i hope this doesn't sound to crazy.

---

### Post by ugm6hr on 2009-04-08
What kind of school work requires you to run a Windows Server?  I know that educational establishments often assume you use Windows as a desktop OS, but to ask students to pay for Windows Server is clearly outrageous.

If the programs will be running on your computer, but you just need to be able to access files on your server, then any server will suffice.

If you *genuinely* need Windows Server, then you may as well just run a single server.  Seems wasteful to have 2 home servers running 24/7 if you could make do with 1.

---

### Post by norman_069 on 2009-04-08
sorry for the confusion but my school doesn't require any server.  I am just wanting to set up a server for my own benefit.  I do however need a windows operating system because my school requires me to use certain windows programs that just don't have a full comparable on ubuntu.

---

### Post by BkkBonanza on 2009-04-08
Ya, you can just setup one server. Both OS can make use of the single server. For file sharing you will want Samba installed on the server. That gives you file sharing compatible with windows. You don't want to use NFS, the linux file sharing system. Clearly if you don't want to buy Windows 2003 server edition (or pirate it?) then you should be using Linux for the server. It will work fine with any machines connected to the network.

You can setup your server at home but getting access to it from the net is another set of issues independent of what server OS you use. Before you even go down that road you need to know if your ISP is blocking access to useful or all ports on your connection. Try a port scan site to check your home from the outside. eg. [https://www.grc.com/x/ne.dll?bh0bkyd2](https://www.grc.com/x/ne.dll?bh0bkyd2)

If you have port 80 open then you are good. If not then you will need to workaround this depending on what ports are open. ISPs like to block ports because you're not supposed to run a server from a home connection (in general). 

Next, you will likely need to arrange for dynamic dns updates so that any name you use will follow your connection ip changes. Doing all this stuff takes a bit of effort but is not too hard. You learn more about networking by doing it.

BTW you can run Windows quite well under Linux using VirtualBox. It's nicer than dual booting. You could even choose to run Windows server under virtualbox in Ubuntu. That would give you a virtual windows server behaving like a second machine on your network but actually living inside your Ubuntu server. I run a couple Windows apps (Lightroom, PS) that I still need and they work great under Ubuntu this way.

---

### Post by hyper_ch on 2009-04-09
It is advised to use a descriptive topic title, that means a topic title that gives some clue about the content in the thread itself...

A generic topic title like "noob here" or "need help" does not help at all. As you may have noticed, just about everyone posting in here has some kind of a problem or issue or question ;)

And it is also adviced to use seperate threads for unrelated problems so that you can mark each one individually as solved.

Or in short terms: Help others to help you ;)

See the forums policy, especially section II.2: [http://ubuntuforums.org/index.php?page=policy](http://ubuntuforums.org/index.php?page=policy)

Also, when you are asked to post output from (config) files or from a command, use [noparse]```

```[/noparse] brackets around (each) output. That makes it also easier to read.

---

### Post by ugm6hr on 2009-04-09
> **norman_069 said:**
> I do however need a windows operating system because my school requires me to use certain windows programs that just don't have a full comparable on ubuntu.

That's fine.  The school does not require server software.

You use Windows applications at school...  But why do you have to run these programs on your server?

I'm not trying to be difficult, but I cannot think of a single desktop application that you would need for school that would be useful to have running on a server.

Honestly, I do not think anyone will be able to give you useful advice unless you clearly state exactly what you want your server to do, and what applications you believe it needs to run.

---

### Post by jigglywiggly on 2009-04-09
I've used ubuntu and windows server. Windows server is relatively easy to use. Setting up activedirectories. BTW just a side note if you are running active directory, use a windows server. Linux can do it, but if you are using windows pc's use a windows server.

---

### Post by norman_069 on 2009-04-09
Thanks for all the info so far,

The reason i want to run aps from the server is so i don't have to have it installed on the computer i may be using at the time, ie school or a misc computer.  That way where ever i am i can log into the server do my work and log out regardless of what computer i may be on.  other than that i am basically looking for a server to store data and be able to stream media where ever i may be.  

hyper_ch sorry about the lack of information in the title.  I am kinda a newb when it comes to forums.  I know exactly what i want but i have a hard time trying to type it out on a computer.

---

### Post by ugm6hr on 2009-04-10
> **ugm6hr said:**
> ... and what applications you believe it needs to run.

From your (still vague) description, it sounds like what you actually want is a Windows *desktop* that you can SSH into remotely, and use as if it was your own local computer.  Not sure that Windows Server is required to do this, and perhaps it is not necessarily the best option.

Of course, the data storage and media serving are genuine *server* applications.  I have heard enterprises can serve desktops from a VM on a server, but that is probably not easy to do ( [http://www.workswithu.com/2008/12/04/ibm-canonical-declair-ubuntu-war-against-windows-office/](http://www.workswithu.com/2008/12/04/ibm-canonical-declair-ubuntu-war-against-windows-office/) ).

A list of applications you want to be able to run on the server would still help to clarify.

---

### Post by norman_069 on 2009-04-10
Sorry about still being vague.  A few examples of applications would be visual studio net, blender, micro station, maybe 3ds max, and logicworks.

Does this help ?

---

### Post by ugm6hr on 2009-04-10
> **norman_069 said:**
> Does this help ?

Errmmm.... Not much :?

Only cos I'm not particularly familiar with any of them.  Nevertheless, they all sound like desktop applications rather than server applications.

If that is a correct assumption, I think your best bet is to use a Windows desktop with all apps installed with a Remote Desktop.  SSH adds a layer of security to that, which I think is also possible for Windows.  If you have a Dynamic IP, something like dyndns will help.

As for the file server stuff, I'm not really sure if any Windows Desktop version has the capacity, but it probably can be done on the same machine.

Other option is to install an Ubuntu server (or desktop) as the file server with SSH / Remote Desktop and a basic window manager / desktop environment, and then install Windows Desktop in a VM within it.

I don't think any of these options will be particularly easy, but I am sure it can be done with a bit of trial and error.

---

### Post by norman_069 on 2009-04-10
Ok, thanks for the info.

I know this won't be easy but it will be a good learning experiment.  I'm going to install ubuntu server 8.04 and see what happens.  Hopefully like you said with a little trial and error things will work out.  

Thanks for all the help.

---

