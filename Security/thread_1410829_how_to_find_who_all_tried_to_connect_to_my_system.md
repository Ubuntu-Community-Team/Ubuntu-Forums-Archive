---
title: "how to find who all tried to connect to my system?"
date: 2010-02-19
forum: Security
---

### Post by kumarldh on 2010-02-19
I googled around and didnt find any answer so here is my question.

How do I find out who all tried to connect or connected to my laptop? 99% machines/laptops on my network are Windows machines, mine is the only full time Linux/Ubuntu and rest are Mac Minis. Today some one tried to connect to my laptop using remote desktop or VNC client and I hurriedly denied the access first time, second time I was able to note down the user name before denying the access but it didnt help me to identify who was the person due to two persons with same name. None of the person is entitled to access my laptop and this seems to be a security risk. So before I take the matter further I need to know who all are trying to access my laptop. I tried to view system logs but that didn't help. Any clue?

---

### Post by Barriehie on 2010-02-19
messages log didn't list src ip's???

---

### Post by kumarldh on 2010-02-19
> **Barriehie said:**
> messages log didn't list src ip's???

Sorry but I didnt understand the logs and basically didnt understand which log file to look at for remote desktop connection/vnc requests.

---

### Post by CharlesA on 2010-02-19
Check the auth.log.

Is there a reason for VNC to be enabled on the laptop?

---

### Post by kumarldh on 2010-02-19
> **CharlesA said:**
> Check the auth.log.

Is there a reason for VNC to be enabled on the laptop?

I checked the auth.log but didn't find any useful info, no IP address is logged in it and most of the strings are as following:
```
Feb 19 18:20:01 kumar CRON[8169]: pam_unix(cron:session): session closed for user smmsp
Feb 19 18:39:01 kumar CRON[8375]: pam_unix(cron:session): session opened for user root by (uid=0)
```
Regarding enabling VNC, IT department guys may need to log in to my laptop.

---

### Post by Kareeser on 2010-02-19
Public-access VNC is a huge security risk, and a password should be set so that any random person can't simply peep into your session.

You say tech support needs VNC to see your machine? Fine, but turn it off when they aren't using it! They have no reason to peep into your machine without your prior consent, so turn off the server and turn it back on when they need a way in.

---

### Post by rookcifer on 2010-02-19
> **kumarldh said:**
> I googled around and didnt find any answer so here is my question.

How do I find out who all tried to connect or connected to my laptop? 99% machines/laptops on my network are Windows machines, mine is the only full time Linux/Ubuntu and rest are Mac Minis. Today some one tried to connect to my laptop using remote desktop or VNC client and I hurriedly denied the access first time, second time I was able to note down the user name before denying the access but it didnt help me to identify who was the person due to two persons with same name. None of the person is entitled to access my laptop and this seems to be a security risk. So before I take the matter further I need to know who all are trying to access my laptop. I tried to view system logs but that didn't help. Any clue?

What are you going to do?  Beat them up?  Just turn off VNC, or else learn how to secure it.

---

### Post by kumarldh on 2010-02-22
@rookcifer: No one can access my machine w/out my consent. The remote desktop is on but you still need my consent to login. The issue is not to beat or jail the guy who did it but how do I know who all are trying to login. 
And thanks for advice, I have turned off VNC but the questions remains, how to find who all tried to connect to my system?

---

### Post by MonkeyZiggurat on 2010-02-22
in the auth.log snippet you posted earlier, after the date and time, it said "CRON" this is to indicate authorisation to a CRON job. If an ssh login was attempted, for example, you'd see sshd written in place of CRON there. Rather than look through the whole file for a rejected VNC attempt, give this a go:

"grep VNC /var/log/auth.log"

depending on when this happened, you might find that your log file has been "recycled" so you might need to have a look in auth.log.1

Agree with the other posters, though, I'd just turn it off:wink:

---

### Post by CharlesA on 2010-02-22
I tested connecting with VNC on an ubuntu desktop VM with no password set. I didn't see anything in the auth.log.

However, if you have it prompt you when someone tries to connect, it will tell you the IP address of the person who is trying to connect:

> A user on the computer ':ffff:192.168.1.12' is trying to remotely view or control your desktop.

Do you want to allow them to do so?

It defaults to refuse.

It would just be easier to turn it off, and turn it on when/if someone needs remote access.

---

### Post by kumarldh on 2010-02-24
Ok Guys, nothing in auth.log.* files. :-)
Apache logs record every request, and in my opinion there must be some thing similar in Ubuntu.

So I take it, if there is a way to see who all tried to connect to the machine, we, means I and all of who answered me, don't know it.

---

### Post by cdenley on 2010-02-24
> **kumarldh said:**
> Ok Guys, nothing in auth.log.* files. :-)
Apache logs record every request, and in my opinion there must be some thing similar in Ubuntu.

So I take it, if there is a way to see who all tried to connect to the machine, we, means I and all of who answered me, don't know it.

As far as I know, the vino VNC server does not log anything anywhere, unfortunately.

[https://bugzilla.gnome.org/show_bug.cgi?id=162465](https://bugzilla.gnome.org/show_bug.cgi?id=162465)

Seeing "who all tried to connect to the machine" is completely dependent on the service they tried to connect to. Most services which authenticate clients as system users (such as ssh) will log attempts in /var/log/auth.log. Other VNC servers create logs in ~/.vnc. Vino does not.

---

### Post by scaine on 2010-02-24
@kumarldh : if you're still keen on fixing this, give x11vnc a try.  Just apt-get it from the repos, then in a terminal, type :

x11vnc -usepw

You'll be prompted to create a password, after which you'll be running a vnc server for the duration of the command (ctrl-c to kill it any time).

It notes the incoming IP address by default, so with a few more options, you'll be able to note incoming username and IP address by checking your logs.

If the IT staff use a specific subnet, then you can tell x11vnc to ignore everything but that subnet.  Something like :

x11vnc -usepw -noxdamage -forever -shared -allow 192.168.1, 192.168.2 -o ~/.vnc/auth.log

Give "man x11vnc" a shot for more options.

---

### Post by doas777 on 2010-02-24
VNC as ubuntu does it, does not use a "login" in the traditional sense, as the session is already initiated, and the remote user is just connecting to a service, which in itself does not run any commands that would be noted in auth (but mabey daemon?).
my guess is that unless the vnc devs specifically told it to log on connect, that there will be no log of access to vino.

try suggesting to your admins, that they tunnel vnc over ssh. that way you will have a log of the ssh connection, and your clickstream is encrypted so it is protected against evasdropping. 

another better alternative to vnc is freenx. it's ssh based and very stable, but it doesn't share a session the way vino does, so they couldn't move the mouse on your screen.

---

