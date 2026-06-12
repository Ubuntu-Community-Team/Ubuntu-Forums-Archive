---
title: "I need to hijack a terminal session"
date: 2011-09-01
forum: Server Platforms
---

### Post by floobit on 2011-09-01
Sometimes I have users that ssh or telnet into a server, open some records on a db, then leave for lunch (potentially locking the records).  Is there a way to hijack their terminal session and send signals to the server as if from their tty/tps in order to back them out safely?  I know I can kick them out directly, but the application they are running is not perfectly stable, and I'd really prefer not to corrupt the db.  Ideally, I'd like a script that sends a bunch of F4 commands in this manner.  I have full root/sudo, of course.  It seems easy to send messages to them from the server to their screen (piping through /dev/pts3 or possibly with ncurses), but I haven't found anything for the other direction.  Ideas?

---

### Post by dtfinch on 2011-09-01
In the future, maybe you can have a script that runs the program with the [screen](http://ss64.com/bash/screen.html) command, and have them use that instead of running it directly. Then you can probably use screen -r to steal their session when needed. Though I've never actually tried that and I don't use screen much.

---

### Post by floobit on 2011-10-28
Yeah, I looked into that.  The issue is that almost all the connections are fine, and I'm not sure I want the overhead of hundreds of screen sessions hanging out after the users have logged off.  They are not very savvy, so often like to close their putties in creative ways that might not interact gracefully with screen.  I especially do not want a situation where one user might have multiple saved screen sessions running because screen decides to start up a new session on the new login.  

Thanks

---

### Post by Jonathan L on 2011-10-28
> **floobit said:**
> Sometimes I have users that ssh or telnet into a server, open some records on a db, then leave for lunch (potentially locking the records).  Is there a way to hijack their terminal session and send signals to the server as if from their tty/tps in order to back them out safely?  I know I can kick them out directly, but the application they are running is not perfectly stable, and I'd really prefer not to corrupt the db.  Ideally, I'd like a script that sends a bunch of F4 commands in this manner.  I have full root/sudo, of course.  It seems easy to send messages to them from the server to their screen (piping through /dev/pts3 or possibly with ncurses), but I haven't found anything for the other direction.  Ideas?

Hi Floobit

If I've understood correctly, the users are logged in over putty from Windows machines to a Ubuntu machine, and they run some text-based/curses-based app which uses F4 to save the database.

Have you considered the answerback sequence?  This is often confused with the terminal-type identification, but was originally designed for telex operators to send their own station ids.  You program it to send your id, and the terminal will transmit it when you press the "send id" button, or when it receives an answerback enquiry from the computer: a control-E.

For your application you program the answerback to be <ESC> OS, which is what the F4 key sends (at least in xtem).  You send it a ctrl-E, and it will be as if the user had typed <ESC> OS.

I tested it with xterm as follows:

Make a file 'redf4':
```
XTerm*answerbackString: \033OS
XTerm*CursorColor: red

```Tell your xserver to accept these resources:
```
xrdb -merge redf4

```Run an xterm, and run your app inside it.  Note that the cursor should be red.
```
xterm

```In that window, find the tty and then run your application

In another window, send the enquiry:
```
printf '\005' > /dev/pts/1

```As you're unlikely to own the target terminal, you'll probably need:
```
sudo sh -c "printf '\005' > /dev/pts/1"
```I tried it with various escape sequences to quit Vi and so on, seems to work exactly like you need.  (The only thing which appeared strange was you can't put a \015 (newline) at the end of the string, only in the middle.)

I see you can set the answerback in putty in its config file: [http://the.earth.li/~sgtatham/putty/0.61/htmldoc/Chapter4.html#config-answerback]("http://the.earth.li/%7Esgtatham/putty/0.61/htmldoc/Chapter4.html#config-answerback")

Any good?

On real terminals you could program the answerbacks in a local mode.  In that era it was considered hilarious to program the answerback to something unscrupulous and trigger it when a victim later sat at that terminal.  Of course legitimate uses also existed, but it was problematic so it's not implemented in a lot of terminal emulators -- I believe gnome-terminal, for example, doesn't have it.

Hope thats helpful.

Kind regards
Jonathan.

---

