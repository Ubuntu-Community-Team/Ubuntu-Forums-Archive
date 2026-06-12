---
title: "Using screen when connecting to Ubuntu server"
date: 2009-09-09
forum: Server Platforms
---

### Post by nickzeff on 2009-09-09
**_The problem_**

I have a Gutsy server which I use for a number of general purposes on my LAN. It stores my media files, peforms backups, runs a web server and MySQL db and various other things.

I administer it solely through terminal sessions from my laptop (running Jaunty). I log in via ssh and perform whatever maintenance or installation I need through the bash shell.

One of the things that used to bug me is that I would start some process running on the server and then want to switch off my laptop or do something that might cause network connectivity to drop, thereby terminating my session and anything that was running on the server.

if you are running time consuming processes on a remote machine, you can use the **nohup** command to ensure that it doesn't get killed when you disconnect, but you have to remember to use it before you start the process off.

I decided to try out **screen**, and I have to say... I love it. I haven't spent ages exploring all it can do, but with a few simple changes, I can now connect to my server and disconnect any time I like, safe in the knowledge that anything I've started off will continue.

**_The solution_**

The first thing I need was connect to my Gutsy server and install screen

```
sudo apt-get install screen
```

For my remote sessions, I log into the server with the username *remoteadmin* ie. I connect from a terminal session on my laptop using **ssh remoteadmin@<servername>**.

This user has a home directory on the server, so I just needed to stick the following command into /home/remoteadmin/.bash_login which, as the name suggests, is run when you log in at the start of the shell session:

```
if [ "$TERM" != "screen" ]; then
  screen -xRR
fi
```

_[Stack Overflow has more information]("http://stackoverflow.com/questions/1075947/can-i-use-gnu-screen-completely-transparently-automatically")_ about this, but basically those params mean "find me a screen session, wherever it was started and reattach to it. if you can't find one, start a new session".

You can have multiple "windows" while in screen, each one a shell doing different things like tailing a log or backing up files. If you're going to do things like this, it helps to have a status bar at the bottom when you're using it. This can be tailored in many ways, but I _[followed the suggestion here]("http://magazine.redhat.com/2007/09/27/a-guide-to-gnu-screen/")_. Remaining in your login user's home folder, create a file called .screenrc which holds your personal screen configuration options, and place the following text in it:

```
hardstatus alwayslastline

hardstatus string '%{= kG}[ %{G}%H %{g}][%= %{=kw}%?%-Lw%?%{r}(%{W}%n*%f%t%?(%u)%?%{r})%{w}%?%+Lw%?%?%= %{g}][%{B}%Y-%m-%d%{W}%c %{g}]'
```


**_Using screen_**

So now, when I log into my server from my laptop, it simply picks up any existing screen session automatically straight after I ssh in.

screen uses magical key combinations to do things like create new windows, detach from sessions and all sorts of things. This can be a bit overwhelming.

The most invaluable key combination you should know about is

<CTRL-a> <?>

(ie. press CTRL and a simultaneously, then the question mark key.)

This gives you a good list of all the keystrokes you can use.


**_Detaching from a session_**

OK, so you don't want to type **exit** at the end of a screen session, you want to just detach, so everything can keep running until you want to re-connect in the future.

Here are three ways of doing this.

<CTRL-a> <d>

This will detach from your screen session and drop you back into the remote shell where you can safely **exit**.

<CTRL-a> <D>

This is what is excitingly known as a _[power detach]("http://www.gnu.org/software/screen/manual/html_node/Power-Detach.html")_ and this detaches you from your screen session and closes the parent process, so you don't have to manually exit the remote shell.

Finally, you could do what I did. I found all these keystrokes a bit annoying. You can remap them, but I couldn't be bothered to go to that trouble. I stuck an alias in the /home/remoteadmin/.bashrc file as follows:

```
alias sd='screen -D'
```

This means that whenever I type sd (stands for screen detach, ok?) it whizzes me out of my session.

If anyone else has some good experiences with screen they'd like to share, please feel free!

---

### Post by grantemsley on 2009-09-09
Check out the package byobu.  It's adds on to screen to:

- automatically reconnect to screen when you log in
- show a status bar at the bottom which shows your different windows, system load, and other things you configure it for.

Makes screen infinitely better.

---

### Post by nickzeff on 2009-09-09
Ohhh! I like the idea of showing system load and things like that. Will definitely check that out. Cheers.

---

