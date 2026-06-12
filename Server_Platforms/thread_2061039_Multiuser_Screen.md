---
title: "Multiuser Screen"
date: 2012-09-21
forum: Server Platforms
---

### Post by LHammonds on 2012-09-21
I need to know how to send the "CTRL+A" command to a screen session in order to give it the ":acladd root" command to allow the session to be taken over by the root account.

I setup a low-rights user to startup a service inside a screen session and added "multiuser on" inside ~/.screenrc which allows the startup of a screen session to be multiuser rather than private.

However, when I have scripts running under the root account (which needs to reboot the server), it needs to access and send commands to the screen session to cleanly exit the service.

For example, I issue this command as the low-rights user when starting a screen session:

screen -d -m -S myapp -t myapp /usr/bin/myapp

This starts up the session in "Multi, detached" mode which is what I want.

However, I have to press CTRL+A inside the session and then type ":acladd root" in order to allow the root user access to this session.

I need to start a multiuser screen session with a low-rights user account and then manipulate that screen session once in a while with the root user.

All of this is to be completely automated via crontab.

So the question is, how do I "send" the CTRL+A command so it can issue the acladd command rather than ending up typing at the services prompt?

I tried pressing CTRL+V inside the VI editor and adding the ^A character in the script but that did not work...it simply added it to the string sent to the console.

**EDIT #1:** Solution was to add the following to the low-rights user's file in ~/.screenrc
```

multiuser on
acladd root

```

**EDIT #2:** Final solution was not to setup screen as multi-user but instead run the command from root as the low-rights user using the "su" command.  Here is an example of a script run by the root user via crontab on how the shutdown command is sent to the screen console, followed by a carriage return:

```

su myjunkuser --command "screen -S myapp -p myapp -X stuff \"shutdown\""
su myjunkuser --command "screen -S myapp -p myapp -X eval \"stuff  \015\""

```

Thanks,
LHammonds

---

### Post by Lars Noodén on 2012-09-21
Both "multiuser on" and "acladd root" can be added inside the low-rights user's .screenrc

---

### Post by LHammonds on 2012-09-21
I wish I had a V8.  Don't know why I didn't think to try that.  Thanks!

I now have that in place in my junkuser account and while logged in with my root user, I can type:

```
screen -ls myjunkuser/myapp
```

And it shows the "Multi, detached" screen that is running.

I know the acl is working because I can now attach to the screen with my root account by typing:

```
screen -r myjunkuser/myapp
```

However, it seems I cannot use the "stuff" command to send key presses.

On my junkuser account, I can type:

```
screen -S myapp -p myapp -X stuff "shutdown"
```

This command will cause the app to shutdown gracefully.

But I cannot get that to work with my root account:

```
screen -S myapp -p myapp -X stuff "shutdown" -x myjunkuser/myapp
```

It says "No screen session found."

LHammonds

---

### Post by Lars Noodén on 2012-09-22
I don't have 'stuff' and can't find it in the repositories but was otherwise able to duplicate your error.  I think it is the -X that is throwing things off.  If you change the sequence of the parameters, it runs fine.  This should work:

```

screen -x myjunkuser/myapp -S myapp -p myapp -X stuff "shutdown"

```

Also, to add to the too brief comment in #2 above, it is also possible to have a separate configuration file just for the multiuser mode.  It can be retrieved by screen using -c

---

### Post by LHammonds on 2012-09-23
> **Lars Noodén said:**
> I don't have 'stuff' and can't find it in the repositories but was otherwise able to duplicate your error.Thanks for the reply.

"stuff" is part of the screen command and basically "stuffs" keyboard key presses into the screen session.

> **Lars Noodén said:**
> I think it is the -X that is throwing things off.  If you change the sequence of the parameters, it runs fine.
Well, it does seem to go a bit further but it acts like it completely ignores the stuff command and simply reconnects to the detached screen.  It does not add the characters to the console like it should...it simply reconnects you to the console which is not what I want it to do.

I've tried a few other combinations by flopping around the order of parameters but still have not found a solution.

> **Lars Noodén said:**
> Also, to add to the too brief comment in #2 above, it is also possible to have a separate configuration file just for the multiuser mode.  It can be retrieved by screen using -c
Thanks.  That won't be needed since this server is dedicated to just this one service and this low-rights user is dedicated to running inside the screen session and for nothing else.

LHammonds

---

### Post by Lars Noodén on 2012-09-23
Thanks for the info about stuff.  There is a lot to screen.  When I try it, I notice that stuff sends the text but does not send a carriage return or newline afterward.  Could that be the problem?


Edit: I've tried it without the -x part and that's when it correctly sends the text, minus CR.

```

screen -S myapp -p myapp -X stuff "shutdown"

```

Edit2: Here's one way to send 'enter'

```

screen -S myapp -p myapp -X stuff "shutdown"$'\012'

```

---

### Post by LHammonds on 2012-09-23
> **Lars Noodén said:**
> When I try it, I notice that stuff sends the text but does not send a carriage return or newline afterward.  Could that be the problem?
I can run the command and it will send the text but ONLY if I run it as the low-rights user that initiated the screen session.

Any attempt by the other account (root), I can only see that the session is there and I can attach to the session but I can never get it to "stuff" the characters from the root account.

If I do not include the "-x myjunkuser/myapp", then it will never even see that a session exists...let alone interact with it in any way.

> **Lars Noodén said:**
> 
I've tried it without the -x part and that's when it correctly sends the text, minus CR.

```

screen -S myapp -p myapp -X stuff "shutdown"

```
Well, that is the magic I am trying to make work...sending the text from the 2nd account.  Are you sure that command was issued from the 2nd user rather than the one that initiated the screen?  If so, that is what I need to replicate.

As for the carriage return, I simply issue a 2nd command like this:

```
screen -S myapp -p myapp -X eval "stuff \015"
```There is also a way to add the special character at the end of the text line while in the VI editor....press CTRL+V, then press ENTER which will add a special ^M character.  However, I would not recommend that method because if you share code with anyone such as these forums, it will not work (copy/paste will see 2 characters, a "^" and the "M" which must be deleted and re-created in a Linux editor.  This would require adding special instructions and cause confusion to anyone that doesn't know better...especially with larger scripts where it can be hidden.

**EDIT: **Just to make sure my testing and various attempts were not bungling me up, I created a new VM and created the low-rights user, logged in as that user, added the following to ~/.screenrc

```

multiuser on
acladd root

```I started the screen session up as the low-rights user.  I then opened another PuTTY session, logged in as my administrator ID, typed "sudo su" to temporarily become the root user and was able to type the following to see the screen session was running:

```

screen -x myjunkuser/myapp -ls

```I saw the screen session and it did in fact show "(Multi, attached)" instead of "(Private)" which means the .screenrc file was correctly found and utilized.

I then tried to see if I could still see the session without the -x by typing the following:

```
screen -ls
```It did not see anything and said "No Sockets found in /var/run/screen/S-root."

Now I try the command with -x and try to send some text through:

```
screen -x myjunkuser/myapp -S myapp -p myapp -X stuff "shutdown"
```It does nothing other than attaching to the session as if I had typed "screen -x myjunkuser/myapp -r"

It is frustrating because this EXACT command works if I were to login with the myjunkuser account instead.

For giggles, I tried:

```
screen -x myjunkuser/myapp
```It simply attached to the session...same as if I added a "-r" option.

To see if it would error out, I tried the following incorrect option:

```
screen -x myjunkuser/myapp -XX
```It gave an error saying "Please specify a command."

Ok, so now I try to encapsulate the entire "command" inside quotes to see if that makes a difference.

```
screen -x myjunkuser/myapp -X "stuff shutdown"
```It now says "No screen session found."

I am beginning to think there is an extra permission that must be granted or "stuff" is not an option that can be used from an account that did not initiate the screen command.   Or maybe the -X command simply does not work with multi-user or is bugged.

LHammonds

---

### Post by Lars Noodén on 2012-09-23
> **LHammonds said:**
> Well, that is the magic I am trying to make work...sending the text from the 2nd account.  Are you sure that command was issued from the 2nd user rather than the one that initiated the screen?  If so, that is what I need to replicate.

No, it was from the first account.  I'm not able to get it from the second account either.  There's got to be a way.

---

### Post by LHammonds on 2012-09-23
> **Lars Noodén said:**
> No, it was from the first account.  I'm not able to get it from the second account either.  There's got to be a way.
Bummer.

I'm going to dig around the screenrc settings to see if I can make heads or tails of it.  However, the one page I saw on the Internet regarding this had a TON of options that made my head spin last time I looked at it.

---

### Post by Lars Noodén on 2012-09-24
If nothing turns up, one option might be to have root use [su](http://manpages.ubuntu.com/manpages/precise/en/man1/su.1.html) to change to the first account before running 'stuff'.

---

### Post by LHammonds on 2012-09-24
> **Lars Noodén said:**
> If nothing turns up, one option might be to have root use [su]("http://manpages.ubuntu.com/manpages/precise/en/man1/su.1.html") to change to the first account before running 'stuff'.
Rather than continuing down a bunny trail, I'll take this solution...which works.

In the scripts that run in crontab as root, I have the following lines which will switch to the low-rights user for just the command to be executed.  No .screenrc setup is required so it can remain a "private" screen rather than fiddle with multi-user.

```

su myjunkuser --command "screen -S myapp -p myapp -X stuff \"shutdown\""
su myjunkuser --command "screen -S myapp -p myapp -X eval \"stuff  \015\""

```Case closed.  1st posted edited to summarize thread's findings.

Thanks Lars
LHammonds

---

