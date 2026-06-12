---
title: "Project: flabber - video portal download program"
date: 2008-04-08
forum: The Cafe
---

### Post by moe pot on 2008-04-08
Hi at all

I wrote an application (called flabber) in Python, that is able to download movies posted on video portals like youtube.com, video.google.com, zdfmediathek (zdf.de, I think you don't know this website ;)) and so on.

Yeah, I know what u r thinking now: Not again a script to download youtube movies. That's no problem to explain: flabber is able to recognize as much as portals you want, because it's expandable with modules. It also supports streaming formats like MMS. RTMP should be supported soon, so flabber is able to download movies of southparkstudios.com. And of course, flabber is able to convert your downloaded movies or dump audio in a .mp3 file. There will also be a GTK GUI soon, written by fred.reichbier.

If you are interested in flabber, take a look at the download page of Launchpad. [https://launchpad.net/flabber/0.0/0.0.4](https://launchpad.net/flabber/0.0/0.0.4) Here you can find ubuntu packages those work great on Hardy (Gutsy isn't tested) and a source package.
Note: PPA is also available: [https://launchpad.net/~flabber/+archive](https://launchpad.net/~flabber/+archive)

For Pythoners: Please don't criticise the python code of 0.0.4. If you want to, criticise the code of the current experimental branch, called trunk hosted on Launchpad.

At the end, please excuse my bad English, I'm not very keen on it ;-)

**edit**
Oh, I forgot: Simple Usage after installation of flabber:
- Open the Terminal
-  Type "flabber --help"
- Example: To download a movie of youtube type: "flabber http://youtube.com/watch?v=OEnNMiISDCM"

Enjoy!
moe pot

---

### Post by kostkon on 2008-04-08
Interesting project. I really like the idea of expanding its download capabilities with modules. And a GUI will be perfect.

I'll follow your project, keep up the good work.

---

### Post by moe pot on 2008-04-09
Thanks a lot! In this case I've to say that "modules" is an incorrect word. It _was_ modules. Now, it's only a file called portals.py with classes. Each class contains code that can get movie name, download link etc. The correct name will be classes, not modules.
But nevertheless, flabber is expandable ;-)

If you want to take a look at the trunk (included with GUI), we can release an alpha or beta version, with an ubuntu package. Otherwise you can simply download the trunk branch via "bzr" and install flabber0.1 by typing "sudo python setup.py install".

---

### Post by Archon810 on 2008-04-10
I'm very interested to see a linux CLI client that can capture rtmp streams, especially in open source. Are you planning on supporting such a feature?

flabber rtmp://something.com/something => something.flv

---

### Post by moe pot on 2008-04-10
First of all, RTMP is proprietary. Because of this it has to be reverse-engineered. The project "rtmpy" [1] has approved such a work, but they aren't finished yet.
If it will be possible to capture rtmp streams, flabber is able to download such files by a video portal link. But it shouldn't be very difficult to capture rtmp streams directly. Why not implement such a feature? ;-) I think we will implement your idea.


[1] [http://rtmpy.org/](http://rtmpy.org/)

---

### Post by Archon810 on 2008-04-10
Are you going to try to reverse engineer it yourself then? When do you think you or rtmpy people will be able to provide a CLI that just accepts an rtmp link?

Thanks!

---

### Post by DoctorMO on 2008-04-10
How does it compare to projects like Miro? will things like the BBC Radio Listen Again and iPlayer be included?

---

### Post by moe pot on 2008-04-11
> **Archon810 said:**
> Are you going to try to reverse engineer it yourself then? When do you think you or rtmpy people will be able to provide a CLI that just accepts an rtmp link?!
No, I'm not. That's the work of rtmpy. I don't know when they are finished, but rtmpy doesn't want to provide a CLI, but a python module used by other python programs (like flabber).


> **DoctorMO said:**
> How does it compare to projects like Miro? will things like the BBC Radio Listen Again and iPlayer be included?
I don't know Miro, but as far as I know, Miro is like a podcatcher and can manage these movies. That's not the work of flabber.

**edit**
Unfortunately the developers come from Germany and from Switzerland, but iPlayer is only allowed for UK users. So we have to use a UK proxyserver or someone of the United Kingom like to help us ;-)

---

### Post by moe pot on 2008-04-14
> **Archon810 said:**
> Are you going to try to reverse engineer it yourself then? When do you think you or rtmpy people will be able to provide a CLI that just accepts an rtmp link?

Thanks!

Good news: our module and GUI writer fred.reichbier has made some investigation and he gambled out, that someone will publish a C++ rtmp client soon. After it has been released, we are able to use this C++ code in our Python code, and it could be possible that flabber is able to handle with RTMP streams really soon ;-)

Greets
moe pot

---

### Post by likeatim on 2008-07-13
> **moe pot said:**
> Good news: our module and GUI writer fred.reichbier has made some investigation and he gambled out, that someone will publish a C++ rtmp client soon. After it has been released, we are able to use this C++ code in our Python code, and it could be possible that flabber is able to handle with RTMP streams really soon ;-)

Greets
moe pot

any news on that?

---

### Post by samuraiCat on 2008-08-22
> **likeatim said:**
> any news on that?


I'd like to second this-- any news? Sounds like what I have been looking for.

---

### Post by billgoldberg on 2008-08-22
I've subscrided to this thread.

For now I use pytube.

When you're a bit further in the development, I might switch.

Those addable modules are the reason I might consider switching.

---

