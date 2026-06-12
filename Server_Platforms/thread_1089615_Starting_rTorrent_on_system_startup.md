---
title: "Starting rTorrent on system startup"
date: 2009-03-07
forum: Server Platforms
---

### Post by smeerbartje on 2009-03-07
Please see the [rtorrent manual]("http://libtorrent.rakshasa.no/wiki/RTorrentCommonTasks#StartingrTorrentonSystemStartup"). If I set up rtorrent to run after start up, how can I open the screen? In other words: my server is booting, rtorrent will run in background. And then? How to open the session which runs in the background?

---

### Post by mrsteveman1 on 2009-03-08
You could try starting the rTorrent program using su then & the job into the background as your own user, then it SHOULD show up when you type jobs.

For instance in whatever script starts rTorrent change the execution line to this:

```
su -c 'rtorrent' <youruser> &
```

That should start the process under your own username and set it as a background job, then when you are in a terminal that job should show up when you run 'jobs' and you can foreground it again.

I haven't tried doing this but in my head it sounds like it should work :)

---

### Post by smeerbartje on 2009-03-10
Thank you for your reply, but I found a very nice how-to which describes the 'screen' tool. Please find it [here]("http://www.rackaid.com/resources/linux-tutorials/general-tutorials/using-screen/"). What I do is this:

[LIST=1]
[*]Open SSH terminal screen
[*]Start the 'screen' tool
[*]Start rtorrent
[*]Press CTRL-A, D(etach)
[*]You now return to the original console instance, which can be close/exit
[/LIST]

Now imagine you're a few days later. Start the console and type screen -r. The previous screen will be re-opened and you're back into that session. Maybe I'm not explaining very well, but please have a look at the previously mentioned how-to for more information.

---

### Post by mrsteveman1 on 2009-03-10
I i know about screen, i just hate using it :D

---

### Post by smeerbartje on 2009-03-10
> **mrsteveman1 said:**
> I i know about screen, i just hate using it :D

Why? I think it's pretty intuitive and fast... well, everybody has it's own preferences :)

---

