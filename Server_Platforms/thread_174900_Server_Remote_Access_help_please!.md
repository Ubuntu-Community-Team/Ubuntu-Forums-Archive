---
title: "Server Remote Access help please!"
date: 2006-05-12
forum: Server Platforms
---

### Post by Jose Catre-Vandis on 2006-05-12
This is all noob stuff probably:

I have a headless "Dapper" server at home, sitting on my lan. At present I have been using the gnome desktop to configure and tweak things using the standard vnc server/client from my other machine. The server is quite old and slow doing this.

I want to switch off gnome and just run from the command line to spped things up, but have not been able to find any details about my remote access requirements, as I understand vnc requires a gnome login and gui to run.

What software do I need on the server / client?
(Access from ubuntu and windows machines both)


Do I need to be logged in on the server for it to work properly (apache / ftp /php etc)?

I f I am looking at a gnome desktop through vnc, what do I do to drop to command line interface, and similarly would I be able to go back to gnome if needed?

Will dapper updates still work, or will I have to manually update?

All help muchly appreciated

---

### Post by jazzmuzik on 2006-05-12
I'm not sure if this will meet all your needs, but I do this:

ssh -2 -Y remoteLoginName@192.168.100.200

This will allow you to log in to the remote machine and execute remote gui programs that you can see on the local machine.

There's also sshfs where you can run local programs and edit remote data as if the data was local.

I'm sure there are other solutions.

---

### Post by Jose Catre-Vandis on 2006-05-12
[QUOTE=jazzmuzik]I'm not sure if this will meet all your needs, but I do this:

ssh -2 -Y remoteLoginName@192.168.100.200

This will allow you to log in to the remote machine and execute remote gui programs that you can see on the local machine.

There's also sshfs where you can run local programs and edit remote data as if the data was local.

I'm sure there are other solutions.[/QUOTE]

Does this assume I have ssh installed on the server? Any client install required?

---

### Post by jazzmuzik on 2006-05-12
The client program is ssh and it is installed by default. The remote program needs to be a daemon (running in the background for those wondering) and that package should be 'openssh-server' and it's not installed by default on a user setup. I'm not sure about a server setup.

---

### Post by Jose Catre-Vandis on 2006-05-12
I installed ssh on the server, and your command worked fine. Great! :-)

and
```
sudo /etc/init.d/gdm stop
```
shuts down the gnome desktop

whilst
```
sudo /etc/init.d/gdm start
```
starts it up again

To stop gdm from loading on boot:
```
update-rc.d -f gdm remove
```

Also followed the XDMCP enable through ssh terminal howto on the forum, which provides a login screen, meaning you don't have to be logged in to access gdm. Need to ensure you enable XDMCP in gdm.conf though.

[http://www.ubuntuforums.org/showthread.php?t=122402](http://www.ubuntuforums.org/showthread.php?t=122402)

All that is left is the update issue. 

either manually

sudo apt-get update
sudo apt-get dist-upgrade -d

or do a cron job as described here:[https://wiki.ubuntu.com/AutoWeeklyUpdateHowTo](https://wiki.ubuntu.com/AutoWeeklyUpdateHowTo)

---

### Post by Jose Catre-Vandis on 2006-05-12
One final thing. If I start a lengthy process on my remote PC, say an update, if I close the terminal, does the update continue? Another example would be to start a big download from the ssh CLI, like a dapper iso. How do I exit the terminal session and leave the download running?

---

### Post by jazzmuzik on 2006-05-12
[QUOTE=Jose Catre-Vandis]One final thing. If I start a lengthy process on my remote PC, say an update, if I close the terminal, does the update continue? Another example would be to start a big download from the ssh CLI, like a dapper iso. How do I exit the terminal session and leave the download running?[/QUOTE]

I've never really done it, but I understand you can put running tasks into the background by adding the ampersand character after a command:

sudo apt-get update &

Something like that.

---

### Post by Jose Catre-Vandis on 2006-05-13
jazzmuzik

thanks for all you help. Much appreciated.

---

### Post by Socratez on 2006-05-13
A handy tool for doing this is called "screen" ... it allows you to attach and detach terminal sessions using keystrokes ... I haven't used it in years but it only took 10 minutes to figure out and it is very useful. I set my ssh login to execute the comman screen upon login and it worked like a charm ... 


Good Luck


Soc

---

### Post by Jose Catre-Vandis on 2006-05-14
screen, excellent, finally figured it and following the GNU Screen tut and reading the screen man told me all I need to know. Once I had understood that typing the command C-a actually meant CTRL+a everything became clear!

Useful extract:

> **Getting started with screen: launching and switching between programs**

Start screen just by typing screen at your favorite command shell prompt.
You'll probably be greeted by a welcome message. Dismiss this and you'll
have with an empty terminal containing a shell prompt, which is pretty much
what you had before you started screen. What happened?

Every program running under screen runs in a window, and every window is 
identified by a unique number. Screen made a new window, numbered it 0, 
and started a command shell inside it. Type something in your new window 
so you'll be able to recognize it when you switch to it later.

Now make another window; this will be window 1. To do this, type C-a c; that is, 
type Ctrl-a and then type c (mnemonic: create window).

Now that you have two windows, try switching between them. To do this, type 
C-a C-a, which will switch you to whichever window you were using before the 
current one. Some other useful window switching methods, which you'll need 
if you plan to run more than two programs:

1. Use C-a n and C-a p to switch to the next or previous window in the list, by number.
2. Use C-a N, where N is a number from 0 to 9, to switch to the corresponding window.
3. Use C-a " to get a full-screen list of windows. You can navigate this list with the arrow 
    keys (or vi-style, with j and k), and pick a window to activate by pressing Enter when it's 
    highlighted. C-a w will give you a small, non-interactive list of windows.

When you're using a window, type C-a A to give it a name. This name will be used 
in the window listing, and will help you remember what you're doing in each window 
when you start using a lot of windows.

Exiting the last program in a window will cause the window to disappear. You can also 
kill misbehaving programs with C-a K.

**Detaching and reattaching: the magic of terminal decoupling**

If you did the exercise above, you have successfully created a screen session. 
You can detach from this session by pressing C-a d. You can also detach just 
by closing the terminal emulator that contains the session. However, keep in 
mind that neither of these actually end your session. All they do is unbind your 
session from the current terminal. All of the programs you started running within 
screen are still running. Really.

Try it: just close whatever terminal emulator you were using to do the exercise above. 
Then log out, and log back in, if you desire. Start up a new terminal emulator, and type 
screen -r (the R, obviously, stands for "reattach"). You'll be right back where you were 
when you detached.

You can probably imagine a lot of good uses for this. You can start all your favorite 
console programs once and just leave them running in a persistent screen session. 
Some people have "screen uptimes" of several months.

One other good use for the detach and reattach is as a console-mode "remote desktop" 
feature. You can detach from a screen session at work, shell into the machine from home, 
and reattach. 

The useful commands:  (remember C = CTRL key, and - = + e.g. with)

C-a c     (CTRL+a then c)   - make a new session
C-a C-a                              - switch between sessions
C-a A                                 - give a session a useful name
C-a "                                  - list all open sessions
C-a K                                 - kill a current session, very useful to help close down screen
screen -wipe                      - remove dead sessions
screen -r                            - type in a terminal to recover your sessions
screen -R                           - as above but recovers "last" session

Oh, and if wanting to use screen to do stuff on a remote machine, run it on the remote machine once you have logged in with ssh (a no brainer I know but then... :-))


So that's me all done, I can drop my server to the command line interface, and restore the Gnome GUI if I want/need to. I can ssh to my server and start a vnc session, and log in, and I can run programs on the remote machine and close down and go to bed, knowing the program is still running. A happy Jose :-)

Thanks to Jazzmuzic and Socratez for your help along the way

---

### Post by Socratez on 2006-05-15
No probs Jose .... you're probably more of a screen pro then I am at this point ... LOL ... Take care

---

