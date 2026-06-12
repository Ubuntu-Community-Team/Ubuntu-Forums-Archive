---
title: "copy terminal to vi, vi to terminal"
date: 2012-07-23
forum: Server Platforms
---

### Post by canucksailor on 2012-07-23
I'm installing a fresh 12.04 server to a clean hdd (no desktop gui.)  How can I copy lines from vi (a text file with commands that were useful and I have saved from previous installations) to the terminal, and also from the terminal to vi (to remember screen output concerning this installation.)  Copying using Nyy in vi does not <shift><ctrl>c to the terminal.

My typing is either fast **or** accurate, and I'm wasting a lot of time "copy typing" all my saved cron jobs, .conf files etc, from another screen on another server.

Thanks - and apologies if this is a "newbie" question.

---

### Post by kennethconn on 2012-07-23
Are you using a client like PuTTY to ssh in?

---

### Post by LHammonds on 2012-07-23
You need to use PuTTY.  You can then copy from the terminal by using the mouse to select the text (auto copies to memory) and then right-click to paste whatever is in memory.

LHammonds

---

### Post by The Cog on 2012-07-23
I'm not aware of any way to do that kind of copy/paste in a tty, maybe because I don't know vi well enough.

I always run up an ssh server as soon as possible, then do all the rest of the setup fron another machine that does have a GUI. Ssh from a GUI terminal allows copy/paste into vi sessions, and you can even use nautilus (thunar im my case) with sftp to drag/drop/copy/edit files.

---

### Post by redmk2 on 2012-07-23
> **canucksailor said:**
> I'm installing a fresh 12.04 server to a clean hdd (no desktop gui.)  How can I copy lines from vi (a text file with commands that were useful and I have saved from previous installations) to the terminal, and also from the terminal to vi (to remember screen output concerning this installation.)  Copying using Nyy in vi does not <shift><ctrl>c to the terminal.

My typing is either fast **or** accurate, and I'm wasting a lot of time "copy typing" all my saved cron jobs, .conf files etc, from another screen on another server.

Thanks - and apologies if this is a "newbie" question.

I also use a remote machine and login using SSH so I can use a ptty, but you can do what you want using only the tty on a single non-gui host.  See [**_[COLOR="DarkSlateGray"]here[/COLOR]_**]("http://www.goworkday.com/2008/12/29/copying-a-block-of-text-from-one-file-to-another-in-vi/")

---

### Post by canucksailor on 2012-07-23
<quote>I also use a remote machine and login using SSH so I can use a ptty, but  you can do what you want using only the tty on a single non-gui host.   See [**_[COLOR=DarkSlateGray]here[/COLOR]_**]("http://www.goworkday.com/2008/12/29/copying-a-block-of-text-from-one-file-to-another-in-vi/")</quote>

Thanks to you all. The "see _here_" is for copying between 2 instances of vi (I do that regularly), not vi and terminal and vice versa.

I was afraid you were all going to say "use SSH/Putty."  I have never been there before.  Just set up a Putty client on my desktop, tried to connect to the new server (and a couple of older ones) and get "connection refused".  Guess this has something to do with the server not being set up correctly (12.04 with latest upgrade), or some sort of certificate.  I'll have to look into that later... but if any of you have a "real quick reference page/cheat sheet" (for the server end and the certificates) that would be helpful.

Again, thanks.

---

### Post by koenn on 2012-07-23
+1 for all the putty or terminal (emulator) + ssh advice. I do that to.

But you can avoid lots of copy/paste by copying (selected) known good conf files over the default ones from  a clean install, eg with scp. 

Also, if you have a list of commands you need to run, you can simply turn that list in to a shell script, copy it over to the server, and execute it. 

You can take that a step further and also include the copy commands for your conf files in that script - eg by putting them on an intranet web server and wget them from the script. This approach is especially worth considering if you have multiple quit similar servers to set up, and as part of a recovery plan.

---

### Post by koenn on 2012-07-23
> get "connection refused"
you need to 
```
sudo apt-get install openssh-server
```
on the server. That's all it takes to get started.

---

### Post by The Cog on 2012-07-23
@redmk2:
Yay, that works. I had a feeling it would be possible in vi.

@canucksailor:
tat trick with vi should get you by. If you want to execute commands that you have in a file, you can just create a file with the commands you want, and then run that filename.

But it will pay off in time if you get that ssh server running and use a  gui client on another machine for the rest of the work.

---

### Post by markbl on 2012-07-23
> **LHammonds said:**
> You need to use PuTTY.  You can then copy from the terminal by using the mouse to select the text (auto copies to memory) and then right-click to paste whatever is in memory.
You can copy and paste in any linux terminal using the left mouse to select text, and then middle click to paste (not right click!).

I find it **very** handy nowadays to use a clipboard manager. I use diodon but there are many for ubuntu (search the packages). The advantage is that they maintain a buffer of your clipboard. So I press ctrl+alt+v and a popup lists all my previous clipboard values which I can select from.

Also note in vi/vim that you can edit another file using ":e /some/other_file" then switch back and forward with ctrl+6. Note that tab completion works when entering the file name here.

---

### Post by LHammonds on 2012-07-24
> **markbl said:**
> You can copy and paste in any linux terminal using the left mouse to select text, and then middle click to paste (not right click!).
I am using Windows 7 and portable PuTTY 0.62.  Right-click is paste for me by default.  Might be a different story for an Ubuntu Desktop.  But regardless, it is done with the mouse, not CTRL+C, CTRL+V as Windows users might expect.

LHammonds

---

### Post by markbl on 2012-07-24
> **LHammonds said:**
> I am using Windows 7 and portable PuTTY 0.62.  Right-click is paste for me by default.  Might be a different story for an Ubuntu Desktop.  But regardless, it is done with the mouse, not CTRL+C, CTRL+V as Windows users might expect.

I last used PuTTY (and windows) many years ago but I think you can set this option in the PuTTY window settings. Middle paste is an xterm convention. PuTTY probably defaults to the windows convention.

---

### Post by codemaniac on 2012-07-24
On a ssh session from Putty , whenever I am editing something on Vim and want to go back to commandline without closing the Vim editor , I use the below command .
```
:!bash
```

When back in bash prompt i can paste the copied command/text from vim by just a right click .Now an exit at bash prompt returns me back to editing with vim , where i was .

---

