---
title: "Citadel groupware"
date: 2005-10-11
forum: Server Platforms
---

### Post by nocturn on 2005-10-11
Has anyone tried this:
[http://www.citadel.org?](http://www.citadel.org?)

I found it by accident (link on a newssite).  It seems to bring most thing hula etc promise and might be an anwer for those asking for groupware solutions here (I'm inlcined to give it a shot if I find the time).

---

### Post by KingBahamut on 2005-10-11
Thats a pretty nice Joomla/Mambo theme on that site. 

No I havent tried it, but I have a customer in need of a groupware suite, so Ill be trying it out later this week, Ill let you know then, nocturn.

---

### Post by nursegirl on 2006-02-02
Did either of you try this?  How did it work?

---

### Post by grizz_granlien on 2006-07-28
Yes I have tried to install it and I can't get it to work but that was before the final release of 6.06 I think it will work in 32 Bit under 5.10 I can't get a lot of stuff workng in 64 Bit. 6.06 for some reason I tried even VHCS and it would not even install in 6.06 under the 64 bit...

Any one get these working please e-mail me at [email]wgranlien@shaw.ca[/email] and if you want I can call you voice and we can go over how you did it and if it works I will be more then glade to phone people or E-Mail them on how it worked and how to set it up...

I am stuck in a rough spot by the way I only have free long distence in Canada and USA and Porariqo or how ever you spell it so E-Mail is better unless you are in me free calling area...

---

### Post by Railsbuntu on 2007-11-04
I installed citadel.

It worked perfectly for sending a mail using SMTP and thunderbird.

However I am not sure I am understanding how it works. The concept of "room" is a bit odd to me. I guess I'll get it sorted out quickly.

---

### Post by ruibernardo on 2007-11-04
I've tried it some time ago. It is very easy to install, just follow [this instructions]("http://www.citadel.org/doku.php/installation:easyinstall:easyinstall"). 

Just beware that if you install citadel in a production server it will disable any SMTP and/or any groupware you have installed and running. You can avoid it on install, but by default it will disable them.

---

### Post by HermanAB on 2007-11-04
Citadel is very good.  It is very efficient and can handle a database with up to 256 terabytes of mail.  Compare that to MS Exchange which bogs down at about 100GB.

I have replaced my complex 5 year old postfix/dovecot/apache/roundcube/wcal/yabb set-up with Citadel.  The result is a zero maintenance system and few hundred very happy users.

Usually, if you can't get Citadel to work, it is because you did not configure the hostname and DNS properly.  If the hostname won't resolve with proper A, PTR and MX records, then Citadel will refuse to send mail.

Citadel is actually quite old.  it started in the early 80s as a BBS, therefore the Chat Rooms idea.  Today, people more commonly use the term Discussion Forum, instead of BBS.  

To Citadel, *everything* is a chat room.  Your email inbox, outbox, send box and so on, are private chat rooms, while a forum is simply a public chat room and a mailing list is a semi-public chat room with a guest list.  The result is a very regular, modular and bug free architecture.

The really nice thing about Citadel is that it takes only about 20 minutes to install it and being self contained, it Just Works (TM).

Cheers,

Herman

---

### Post by Railsbuntu on 2007-11-05
> Just beware that if you install citadel in a production server it will disable any SMTP and/or any groupware you have installed and running.

I don't know if it is related with Citadel, but my apache server won't shut down properly now.

Here is the thread I opened about this issue: [http://ubuntuforums.org/showthread.php?t=602278]("http://ubuntuforums.org/showthread.php?t=602278")

---

### Post by HermanAB on 2007-11-05
Well, it is kinda obvious that you cannot run multiple services on the same ports...

Citadel is a self contained mail system and includes a very nice web server for its web interface.  I am mixing things by running Apache http on port 80 and Citadel secure web mail https on port 443.  That requires careful configuration of Citadel and Apache.  Apache likes to glom onto every address and port and you got to prevent that for things to work together.

If you have a high trafic mail server or web site, then it is best to keep things on separate machines, since the load characteristics are such that they could affect each other.

---

### Post by Railsbuntu on 2007-11-05
Alright, I will check which ports are being used by whom. Thanks.

---

### Post by jimbojones on 2007-11-05
With Herman's help I was able to get Citadel working on my box and I like it.  I originally I tried to use the deb packages and I had nothing but trouble with the init.d scripts.  I then used the newer ez-install and like Herman said about 20 minutes and it was up and running :)

---

### Post by Railsbuntu on 2007-11-05
Hi, here is how I did:

First update /etc/apt/sources.list by adding the following depot:
```
deb [http://ubuntu.citadel.org/ubuntu](http://ubuntu.citadel.org/ubuntu) gutsy main
```
Depending on your distro you can adjust gutsy/feisty/etc...

```
sudo apt-get update
sudo apt-get install citadel-suite
```

Then you have to answer questions, in my case I answered:
[LIST=1]
[*]Internal
[*]8504
[*]443
[*]0.0.0.0
[*]Administrator
[*]No
[/LIST]

Then I had to wait 15-20 minutes, and the installation was done. However I am having problems between Citadel and Apache, so my installation is certainly flawed, but it can be a good starting point. :)

---

### Post by HermanAB on 2007-11-05
I fixed the fight between Citadel and Apache using iptables redirection.  I installed Citadel on ports 8080 and 8000 so I could test it independently, then I disabled the Apache SSL engine and used an iptables redirect to send port 443 to 8000, my chosen https port for Citadel.  

You can try something similar to get it sorted out - keep them separated, till the coast is clear, then glue them together using iptables.  
This way, I convinced http to go to Apache while https goes to Citadel.

Cheers,

H.

---

### Post by jimbojones on 2007-11-05
Thats the same way I had installed it and I was unable to do  /etc/init.d/citadel stop, would just get ...............
I thought I had mine installed on a different port than apache, but regardless I am curious to see what you find.  Note that once I scraped the .deb install and did the ez-install all was fine

> **Railsbuntu said:**
> Hi, here is how I did:
First update /etc/apt/sources.list by adding the following depot:
```
deb [http://ubuntu.citadel.org/ubuntu](http://ubuntu.citadel.org/ubuntu) gutsy main
```
Depending on your distro you can adjust gutsy/feisty/etc...

```
sudo apt-get update
sudo apt-get install citadel-suite
```

Then you have to answer questions, in my case I answered:
[LIST=1]
[*]Internal
[*]8504
[*]443
[*]0.0.0.0
[*]Administrator
[*]No
[/LIST]

Then I had to wait 15-20 minutes, and the installation was done. However I am having problems between Citadel and Apache, so my installation is certainly flawed, but it can be a good starting point. :)

---

### Post by Railsbuntu on 2007-11-05
Here is the result of the **netstat -lnp** command:

```
sudo netstat -lnp
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 0.0.0.0:993             0.0.0.0:*               LISTEN     3877/citserver
tcp        0      0 0.0.0.0:995             0.0.0.0:*               LISTEN     3877/citserver
tcp        0      0 0.0.0.0:2020            0.0.0.0:*               LISTEN     3877/citserver
tcp        0      0 127.0.0.1:3306          0.0.0.0:*               LISTEN     3806/mysqld
tcp        0      0 0.0.0.0:587             0.0.0.0:*               LISTEN     3877/citserver
tcp        0      0 0.0.0.0:110             0.0.0.0:*               LISTEN     3877/citserver
tcp        0      0 0.0.0.0:143             0.0.0.0:*               LISTEN     3877/citserver
tcp        0      0 0.0.0.0:465             0.0.0.0:*               LISTEN     3877/citserver
tcp        0      0 0.0.0.0:504             0.0.0.0:*               LISTEN     3877/citserver
tcp        0      0 0.0.0.0:8504            0.0.0.0:*               LISTEN     3885/webserver
tcp        0      0 0.0.0.0:25              0.0.0.0:*               LISTEN     3877/citserver
tcp        0      0 0.0.0.0:443             0.0.0.0:*               LISTEN     3888/webserver
tcp6       0      0 :::80                   :::*                    LISTEN     3972/apache2
tcp6       0      0 :::22                   :::*                    LISTEN     3712/sshd
udp        0      0 0.0.0.0:68              0.0.0.0:*                          3253/dhclient3
Active UNIX domain sockets (only servers)
Proto RefCnt Flags       Type       State         I-Node PID/Program name    Path
unix  2      [ ACC ]     STREAM     LISTENING     12803    3877/citserver      /var/run/citadel/citadel.socket
unix  2      [ ACC ]     STREAM     LISTENING     12814    3877/citserver      /var/run/citadel/lmtp.socket
unix  2      [ ACC ]     STREAM     LISTENING     12816    3877/citserver      /var/run/citadel/lmtp-unfiltered.socket
unix  2      [ ACC ]     STREAM     LISTENING     12580    3806/mysqld         /var/run/mysqld/mysqld.sock
unix  2      [ ACC ]     STREAM     LISTENING     12759    3918/dovecot        /var/run/dovecot/dict-server
unix  2      [ ACC ]     STREAM     LISTENING     12761    3918/dovecot        /var/run/dovecot/login/default
unix  2      [ ACC ]     STREAM     LISTENING     12766    3918/dovecot        /var/run/dovecot/auth-worker.3931

```

What i don't understand is who is listening on port 443? What is the program called webserver?

The ssl module is disabled in apache, and here is my /etc/apache2/ports.conf file:
```
Listen 80

<IfModule mod_ssl.c>
    Listen 443
</IfModule>

```

I guess we are getting closer to the problem :)

EDIT: I noticed /var/run/dovecot/dict-server and whatsoever are listening, but dovecot is not installed on my system. Is that citadel that runs a program called dovecot?

---

### Post by HermanAB on 2007-11-05
webserver == webcit, the Citadel webmail/BBS server.

So that looks OK to me.

If you do:
[http://yourdomain](http://yourdomain)
then you should get to Apache on port 80.

and if you do:
[https://yourdomain](https://yourdomain)
then you should get to Citadel on port 443.

Cheers,

H.

---

### Post by Railsbuntu on 2007-11-05
So I rebooted my computer to try a startup script for a RoR application.

I don't know what happened, both apache and citadel are broken!

When I pointed my browser to go to [http://mydomain](http://mydomain). I got no response. **netstat -nlp** told me that apache was not running. 
```
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 0.0.0.0:993             0.0.0.0:*               LISTEN     3882/citserver
tcp        0      0 0.0.0.0:995             0.0.0.0:*               LISTEN     3882/citserver
tcp        0      0 0.0.0.0:2020            0.0.0.0:*               LISTEN     3882/citserver
tcp        0      0 127.0.0.1:3306          0.0.0.0:*               LISTEN     3811/mysqld
tcp        0      0 0.0.0.0:587             0.0.0.0:*               LISTEN     3882/citserver
tcp        0      0 0.0.0.0:110             0.0.0.0:*               LISTEN     3882/citserver
tcp        0      0 0.0.0.0:143             0.0.0.0:*               LISTEN     3882/citserver
tcp        0      0 0.0.0.0:465             0.0.0.0:*               LISTEN     3882/citserver
tcp        0      0 0.0.0.0:3000            0.0.0.0:*               LISTEN     3885/ruby
tcp        0      0 0.0.0.0:504             0.0.0.0:*               LISTEN     3882/citserver
tcp        0      0 0.0.0.0:25              0.0.0.0:*               LISTEN     3882/citserver
tcp6       0      0 :::22                   :::*                    LISTEN     3717/sshd
udp        0      0 0.0.0.0:68              0.0.0.0:*                          3272/dhclient3
Active UNIX domain sockets (only servers)
Proto RefCnt Flags       Type       State         I-Node PID/Program name    Path
unix  2      [ ACC ]     STREAM     LISTENING     12578    3811/mysqld         /var/run/mysqld/mysqld.sock
unix  2      [ ACC ]     STREAM     LISTENING     12715    3882/citserver      /var/run/citadel/citadel.socket
unix  2      [ ACC ]     STREAM     LISTENING     12726    3882/citserver      /var/run/citadel/lmtp.socket
unix  2      [ ACC ]     STREAM     LISTENING     12728    3882/citserver      /var/run/citadel/lmtp-unfiltered.socket

```

So I started apache by hand, and it worked. Apache was added to the previous list.

So I decided to go to: [https://mydomain](https://mydomain), nothing responded. As you can see from the previous netstat output, webserver is no longer listening on port 443.

What happened? :confused:

And by the way, dovecot has also disappeared...

---

### Post by HermanAB on 2007-11-05
It looks like webcit died.  Try restarting it.  There is a script in /etc/rc.d/init.d, so it should be something like:
# service webcit restart

The only times I had trouble with webcit was when it was doing battle with Apache.  Since I managed to fix that, it is stable.

Cheers,

H.

---

### Post by Railsbuntu on 2007-11-06
I removed my RoR startup script and everything got back in business. I still have this issue when shutting down apache.

---

### Post by Railsbuntu on 2007-11-06
I deciced to shutdown citadel to see what would happen, here is the result:
```
sudo /etc/init.d/citadel stop
.........................................

```
The dots carry on for ever. So I have to break it with ctrl+c

However **netstat -nlp** returns:
```
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 127.0.0.1:3306          0.0.0.0:*               LISTEN     3805/mysqld
tcp        0      0 0.0.0.0:80              0.0.0.0:*               LISTEN     4571/apache2
tcp        0      0 0.0.0.0:3000            0.0.0.0:*               LISTEN     4035/ruby
tcp        0      0 0.0.0.0:8504            0.0.0.0:*               LISTEN     3884/webserver
tcp        0      0 0.0.0.0:443             0.0.0.0:*               LISTEN     3887/webserver
tcp6       0      0 :::22                   :::*                    LISTEN     3711/sshd
udp        0      0 0.0.0.0:68              0.0.0.0:*                          3250/dhclient3
Active UNIX domain sockets (only servers)
Proto RefCnt Flags       Type       State         I-Node PID/Program name    Path
unix  2      [ ACC ]     STREAM     LISTENING     12591    3805/mysqld         /var/run/mysqld/mysqld.sock
unix  2      [ ACC ]     STREAM     LISTENING     12770    3917/dovecot        /var/run/dovecot/dict-server
unix  2      [ ACC ]     STREAM     LISTENING     12772    3917/dovecot        /var/run/dovecot/login/default
unix  2      [ ACC ]     STREAM     LISTENING     12777    3917/dovecot        /var/run/dovecot/auth-worker.3930

```
citserver was stopped, but webserver (which is part of citadel) is still running. Hmmm...

Let's try:
```
sudo /etc/init.d/webcit stop
```

And the corresponding netstat-nlp:
```
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 127.0.0.1:3306          0.0.0.0:*               LISTEN     3805/mysqld
tcp        0      0 0.0.0.0:80              0.0.0.0:*               LISTEN     4571/apache2
tcp        0      0 0.0.0.0:3000            0.0.0.0:*               LISTEN     4035/ruby
tcp6       0      0 :::22                   :::*                    LISTEN     3711/sshd
udp        0      0 0.0.0.0:68              0.0.0.0:*                          3250/dhclient3
Active UNIX domain sockets (only servers)
Proto RefCnt Flags       Type       State         I-Node PID/Program name    Path
unix  2      [ ACC ]     STREAM     LISTENING     12591    3805/mysqld         /var/run/mysqld/mysqld.sock
unix  2      [ ACC ]     STREAM     LISTENING     12770    3917/dovecot        /var/run/dovecot/dict-server
unix  2      [ ACC ]     STREAM     LISTENING     12772    3917/dovecot        /var/run/dovecot/login/default
unix  2      [ ACC ]     STREAM     LISTENING     12777    3917/dovecot        /var/run/dovecot/auth-worker.3930

```
webserver and citserver have now surrendered.

Now it is time to try to shutdown:
```
sudo shutdown -h now
```

... silence in the room please ...

```
System halted.
```
Huray! :popcorn:

Now it is clear that it is not apache giving trouble but citadel. I will try to look for more on that.

PS: what in hell is this dovecot doing here? I swear in front of Gnu almighty I have never installed it. :confused:

EDIT: found on the citadel mailing list:
[[Citadel Support] Re:Ubuntu Gutsy problems]("http://www.mail-archive.com/room_citadel_support@uncensored.citadel.org/msg02883.html")

HermanAB, on which distro do you have citadel installed? Probably the installer is broken for 7.10?

---

### Post by jimbojones on 2007-11-06
Railsbuntu, check out my above post, I had the same problem using the .deb files.  Removed everything and used the EZ-Install and all is good now.  Same problem happened in Feisty, Gutsy Beta and now Gutsy Final, the /etc/init.d/citadel script doesnt see the process stopping and it just hangs, thus holding up your reboot/shutdown request.  I had brought that up ont he citadel forums and was not able to get a fix, but like I said the EZ-Install works fine for me on 7.10

---

### Post by Railsbuntu on 2007-11-06
Houston we have a problem.

I did:
```
sudo apt-get autoremove citadel-suite
```

Rebooted the computer

But the citadel daemons are still running!!! :mad:

On the citadel mailing list, a gutsy user has posted that he was also unable to uninstall the citadel packages from his computer, and I am having the same problem :-?

Any way, I am currently installing citadel using the easy install instructions, let's see what happens. I see warnings appearing on the screen during the installation of libical...


EDIT: jimbojones, sorry I missed your post where you said you had the same problem when doing /etc/init.d/citadel stop. I must have posted without previously refreshing the webpage.

EDIT2: the ubuntu package definitely doesn't work, this issue must be addressed to citadel and/or ubuntu developpers, or at least a warning should be written somewhere to avoid having other people wasting time installing this package. It could be Ubuntu's new upstart system which is not working well with the citadel package and scripts.

---

### Post by jimbojones on 2007-11-06
Its ok, just wanted to save you some aggravation, I went through the same thing.  Now that you mention it I had trouble removing it too, I had to search for any reference of cit* and remove alot by hand.  I ended up redoing the server and did a fresh EZ_Install and that has been running flawless.  Those posts you saw might be me, I had posted up alot of questions about that script but they were unable to duplicate the problem :confused:

---

### Post by Railsbuntu on 2007-11-06
Argh! Reinstalling the server... Happily I have written down all the steps I took to install all the apps on it, and I will be receiving some additional Ram and harddrive, so it won't be too annoying.

I am fairly new to Ubuntu. Is there a way to know what steps apt-get performs for a given package (hint: citadel) so that I can do the backward operations to remove completely the package by hand?

PS: I am having all sorts of warning on the screen while compiling citadel :-?

EDIT: this is where the installer has stopped, now I have all these dots being printed. Is it looking bad?
```
/usr/local/ctdlsupport/include/ical.h:97:1: warning: "PACKAGE_TARNAME" redefined
In file included from webcit.h:3,
                 from setup.c:11:
sysdep.h:95:1: warning: this is the location of the previous definition
In file included from webcit.h:87,
                 from setup.c:11:
/usr/local/ctdlsupport/include/ical.h:100:1: warning: "PACKAGE_VERSION" redefined
In file included from webcit.h:3,
                 from setup.c:11:
sysdep.h:98:1: warning: this is the location of the previous definition
  Complete.
* Configuring your system ...
[: 475: ==: unexpected operator
This is a new Citadel installation.
.............................................................................................................

```

EDIT: the dots seem to be printing on for ever...

I had to do ctrl+C, so it skipped the configuration questions. However i was able to do /etc/init.d/citadel stop.

Unfortunately, I still can't shutdown correctly the server. The old citadel package must still be sticking around somewhere. So I won a ticket to reinstall my whole server...

---

### Post by jimbojones on 2007-11-06
i would search for any files on your system starting with  cit*  and remove anything citadel related by hand, and remove the scripts in /etc/init.d for citadel.  The packages dont remove properly because of that server not shutting down.  Mine actually said I had a corrupted package and it was a nightmare to get straightened out.  I dont know how to see where the files installed, hopefully someone can shed some light on that.

 Here is Citadels page for uninstalling
[http://www.citadel.org/doku.php/faq:installation:how_do_i_uninstall_citadel](http://www.citadel.org/doku.php/faq:installation:how_do_i_uninstall_citadel)

and check this for file structure
[http://www.citadel.org/doku.php/documentation:file_layout](http://www.citadel.org/doku.php/documentation:file_layout)

---

### Post by Railsbuntu on 2007-11-06
Excellent! Perfect! Brilliant! Amazing! Awesome!

I was able to uninstall the old-broken citadel, it took me a lot of apt-get remove and purging and all that stuff. Then I was able to install using the EZ install, and now my server has apache and Citadel working like a charm.

And I can shutdown properly now :guitar:

I highly recommend citadel and the install using the EZ steps.

Thanks HermanAB and jimbojones for your precious help :KS

---

### Post by Railsbuntu on 2007-11-06
One more problem. I tried to send an email with thunderbird, and it never arrives. Inside citadel, I see that the email hasn't been sent off and I get the following error message:

> The IP you’re using to send email is not authorized

Is it my ISP which is blocking me now?

Sending email worked with the citadel package.

---

### Post by Railsbuntu on 2007-11-06
jimbojones suggested me to try to send an email through webcit, and it worked.

I think it is when Citadel asked me for which IP adresses it would be listening, I entered the IP of my server. I should have instead typed in 0.0.0.0

But in the administration page, I have:
> Server IP address (0.0.0.0 for 'any') -> 0.0.0.0

Is that it?


EDIT: [SOLVED]

In thunderbird I configured the client to connect to citadel through TSL using port 587, and it worked.

---

### Post by artcancro on 2007-11-07
> **epimeteo said:**
> Just beware that if you install citadel in a production server it will disable any SMTP and/or any groupware you have installed and running. You can avoid it on install, but by default it will disable them.

Citadel will *offer* to disable existing SMTP/IMAP/POP services you have running.  It will never do this without your permission.

Also, the list of services it will offer to disable has been pared down a bit.  Now it only includes services which are likely to have been included as part of the operating system's default installation.

It is our goal for Citadel to become *the* open source "Exchange killer" -- a superstar like Samba or Apache.  Everyone's participation is both welcome and appreciated.

---

### Post by artcancro on 2007-11-07
> **Railsbuntu said:**
> In thunderbird I configured the client to connect to citadel through TSL using port 587, and it worked.

This sounds as if Citadel was not able to bind to port 25, at least not on the IP you're trying to connect to.  (Or if you are remote, it's being blocked by your ISP?)

netstat -lnp will tell all.

---

### Post by HermanAB on 2007-11-07
A typical comment I hear from a new Webcit user is: "Wow, this is easy!"

To my mind, Citadel absolutely is the best email system out there - due in no small part to Easy Install.

---

### Post by dothebart on 2007-11-07
ok, some aditions have been made to the citadel init script so it will succeed in any case. for the ones having trouble to remove the debs, there are two points.

There are several debs to enable distribution of the citadel components over several (virtual) machines. Or maybe you just want the commandline client and use it remote.. the suite package brings you all of them by just depending on them.
Right under the apt line you've used to install them, there's a list of them:
[http://www.citadel.org/doku.php/installation:debian#packages.available.here.and.their.content](http://www.citadel.org/doku.php/installation:debian#packages.available.here.and.their.content)

Many debs require to have a MTA installed, which is what easy install won't provide you. So you have to keep an mta installed, which might come back to life on some upgrade, and put citadel out of service.

Re dovecot... Dovecot is an imap server, which the citadel server will conflict with, and thus make apt remove it. maybe thats the reason why it didn't come up after the reboot again, it was gone. File a bug against the package, it should have stopped it on removal.

---

### Post by ruibernardo on 2007-11-07
> **artcancro said:**
> Citadel will *offer* to disable existing SMTP/IMAP/POP services you have running.  It will never do this without your permission.
That's exactly what I ment. If the user installs citadel and just press enter on all questions (like some users are likely to do and some users here must have done) it will, by default...> **epimeteo said:**
> disable any SMTP and/or any groupware you have installed and running. You can avoid it on install, but by default it will disable them.Anyway, when it tries to disable these service, it fails to do it with some services (has we can see it on this thread).

I really just wanted to make clear what the default install does. Sorry if you didn't understood.

---

### Post by Railsbuntu on 2007-11-07
Hi guys,

Concerning Dovecot:
```
dpkg --list | grep dove
ii  dovecot-common                        1:1.0.5-1ubuntu2           secure mail server that supports mbox and ma
rc  dovecot-imapd                         1:1.0.5-1ubuntu2           secure IMAP server that supports mbox and ma
rc  dovecot-pop3d                         1:1.0.5-1ubuntu2           secure POP3 server that supports mbox and ma

```

So I uninstall these packages, then:
```
dpkg --list | grep dove
rc  dovecot-common                        1:1.0.5-1ubuntu2           secure mail server that supports mbox and ma
rc  dovecot-imapd                         1:1.0.5-1ubuntu2           secure IMAP server that supports mbox and ma
rc  dovecot-pop3d                         1:1.0.5-1ubuntu2           secure POP3 server that supports mbox and ma

```
I still get the same packages! This dovecot thing is insane! I will check if it is installed by default on Gutsy. Anyway at this very moment, it is not annoying me, so I will take care of it another time. I swear I have never in my life installed dovecot or any related package :confused:


There is a lot of new info you are bringing us, I'll go through it over the weekend. Now I am playing with citadel :)

Concerning the SMTP on port 25, I have my bug tracking app running on my server and which notifies me by sending emails, it is configured to use port 25 and it works. It is only when the server is accessed remotely (but still in the same LAN) on port 25 that I get this "forbidden IP" message.

Thanks for your help :KS

---

### Post by dothebart on 2007-11-07
ii -> installed
rc -> removed config still on the system

rc can be removed with dpkg --purge packagename

you can make it use lmtp.sock, or the recipient should be local to your citadel server.

---

### Post by artcancro on 2007-11-08
> **epimeteo said:**
> Anyway, when it tries to disable these service, it fails to do it with some services (has we can see it on this thread).

Ok ... if you know of any services to disable that ought to be on the list and aren't, do let us know and they will be added.  Thanks for your time and support!

---

### Post by ruibernardo on 2007-11-08
> **artcancro said:**
> Ok ... if you know of any services to disable that ought to be on the list and aren't, do let us know and they will be added.  Thanks for your time and support!

Please read my posts. I don't use citadel, just installed it once and warned people here that it disables services by default. As you can see, it happened.

Can you tell the users who got problems here where they can get help or how to solve them or how they can help citadel development?

That would be a positive thing to do...
> **artcancro said:**
> for Citadel to become *the* open source "Exchange killer" -- a superstar like Samba or Apache. Everyone's participation is both welcome and appreciated.

Cheers.

---

### Post by HermanAB on 2007-11-08
Here you go:
[http://www.citadel.org/doku.php?id=mailing_lists](http://www.citadel.org/doku.php?id=mailing_lists)
[http://uncensored.citadel.org/](http://uncensored.citadel.org/)
[http://bugzilla.citadel.org/](http://bugzilla.citadel.org/)

---

### Post by Railsbuntu on 2007-12-07
Edited.

---

### Post by Railsbuntu on 2007-12-07
If I put my citadel server on the web. How can I restrict sending emails through my server?

Currently I have tested, and sending email through port 25, with no username and no password works. This means that any spammer can use my citadel server to send spam.

I'd like to restrict sending email using smtp to usrs that are registered  in my citadel db? I can't find any option for that. I thought that local host aliases were meant for that, but even if I specify an alias I can still send emails from another computer that is not aliased.

Thanks

EDIT: I deactivated listening on port 25, but I can still send emails using port 465 and anonymous connection...

EDIT2: also deactivate listening on port 465, and only leave port 587. This port requires authenticated connection.


New question: can I force my users to use a secured TLS connection?

---

### Post by Wizard of Aahz on 2007-12-10
Rails,

I'm grabbing a couple of answers from the citadel documentation which you can find on Citadel.org..

To control overall access to internet email one uses the global configuration option 11. This only allows network users - Access Level 4 to have access to sending internet email. Keep your new users to a level below this using option 6 - Initial level for new users. This way only registered and approved users can send, defeating the spammers. 

I'm pretty sure there's a way to control TLS only access. I think I've been on a couple of systems where ssl was required,  but one of the other people will need to step you through that. 

-Aahz

---

### Post by Railsbuntu on 2007-12-10
Ok I get it now. I didn't understand at first glance how this "user level" worked. I'll check again the documentation.

---

### Post by knytphal on 2007-12-12
I have been using citadel for a couple of years now, however I have recently come into an issue.  I can no longer send email, and get the "The IP you're using to send email is not authorized" error message.

I did not used to have this issue and am not sure when I became not able to send mail.  I can still receive mail, however.  

I have updated my MX record with my DNS (I use no-ip premium).

The settings in Citadel have not changed, I've double checked those.  Like I say, I've gone from being able to send to not being able to send.

I am awaiting a response from my service provider to see if they are blocking ports, but I don't think they are.  They never have - in fact they will let you hang yourself on bandwidth usage, as they love to charge you for going over!

---

### Post by freebeer on 2007-12-12
> **knytphal said:**
> I have been using citadel for a couple of years now, however I have recently come into an issue.  I can no longer send email, and get the "The IP you're using to send email is not authorized" error message.


My guess would be that it's an authentication problem.  IPs are tightening down their security it seems (to combat spam) and the IP you're routing your mail to probably needs authentication now.  Or something related to it.

---

### Post by HermanAB on 2007-12-12
Check your DNS and ensure that there is a PTR record (Reverse DNS).

Cheers,

Herman

---

### Post by knytphal on 2007-12-12
> **freebeer said:**
> My guess would be that it's an authentication problem.  IPs are tightening down their security it seems (to combat spam) and the IP you're routing your mail to probably needs authentication now.  Or something related to it.

The only server that I'm sending mail through is my own - I don't route through my provider.  I got a response from my ISP, they don't block anything except the MS Exchange and Network sharing ports, so it isn't that.

How would I go about finding out if there is some kind of middle man server that I'm relaying through, even though I have not configured any kind of relay except my own?

EDIT:
OK.  I guess that the google mail account that I was sending a test email to is the culprit, in that google does not like address that don't reverse properly - I guess due to the no-ip dynamic dns name thing. It reverses to my providers name and not my email domain.  Is there a way to remedy that?

---

### Post by Railsbuntu on 2007-12-12
If this helps:

My network gets access to internet using a dynamic IP. My citadel server is on that network also. I just sent an email to one of my gmail box, to try and replicate your problem, and the email arrived in the spam folder, but it still arrived, which is a success. However I don not use no-ip.

Try sending an email using thunderbird (or any other client) to one of your accounts on the server (don't go to the outside world). 

In my case, my citadel server is hosted on a server called "ubuntu", and one of my accounts on citadel is called "Administrator", so to test sending emails using only the LAN, I send to: administrator@ubuntu

See if it works for you. Let's try and isolate the problem.

---

### Post by HermanAB on 2007-12-13
If you wish to run a mail server and have it work properly, then you must have a proper domain name service.

Also note that Citadel will refuse to send mail if the hostname is not defined properly as a FQDN.  Type 'hostname' and see what it returns.  It has to be of the form 'server.example.com' and the DNS must match.

Cheers,

Herman

---

### Post by knytphal on 2007-12-13
> **Railsbuntu said:**
> If this helps:

My network gets access to internet using a dynamic IP. My citadel server is on that network also. I just sent an email to one of my gmail box, to try and replicate your problem, and the email arrived in the spam folder, but it still arrived, which is a success. However I don not use no-ip.

Try sending an email using thunderbird (or any other client) to one of your accounts on the server (don't go to the outside world). 

In my case, my citadel server is hosted on a server called "ubuntu", and one of my accounts on citadel is called "Administrator", so to test sending emails using only the LAN, I send to: administrator@ubuntu

See if it works for you. Let's try and isolate the problem.

That's the thing, whenever I would send mail to my gmail account it would go into the spam folder - I did not have an issue with that.  But now it just flat out refuses to send there at all.  

I can send email to another account (at KU) and it goes through with no problem.  I can send email within my system between users no problem.  I have Thunderbird setup as well and it can send to KU and within the system no problem.  Just can't send to that gmail address, and I would of course assume there are other servers that are not going to allow either.

I tried again using Thunderbird to send to the gmail account, and so far it is in limbo - I have yet to get the error nor has it gone through yet.

EDIT:
My hostname is set up as server.example.com, as returned by the hostname command (granted, it isn't really server.example.com, but something else).

---

### Post by knytphal on 2007-12-13
First, sorry for the double post...

I just sent email to one of my sneakemail addresses (that goes to the gmail account) and it went through just fine.  So gmail just doesn't like my server as the source then.

---

### Post by HermanAB on 2007-12-13
It is most likely the PTR record that is missing from your DNS setup causing this.  Most mail servers only accept mail from another serrver if the reverse DNS resolves.

---

### Post by tiger74 on 2008-02-05
I'm confused with Citadel's Room concept.
Is it like a 'Forum' as a whole?
Then we create cathegories?
And.. what about the email? Where is it?
What if we just want to create a simple mail server with:
- domain
- users
- mailing list (is mailing list a room?)
:confused:

---

### Post by HermanAB on 2008-02-06
It should not be confusing at all.  The software is object oriented and *everything* is a chat room.  Some rooms can be viewed in multiple ways: email style or bulletin board style.  Then there are the usual special rooms like calendars, notes, address books, configuration, administration, instant messages and so on.

Your email is in private rooms, called inbox, sent - the usual names.  You can also have mailing lists, which are private rooms with invite access lists and you can have public rooms which are free for all.

Really, it is just a naming convention, but the hotel with many floors and a public lobby does make sense once you are using it.  For example, I create a floor for each company that I host email for.  They can then create rooms on that floor and go crazy to sort out their email into client accounts, or whatever the heck makes sense to their business - these show up as mail folders in an IMAP mail client.  Provided that they keep the rooms private and only invite people that need to read them, no-one else can see those rooms.

It all works very well with Thunderbird and Outlook with IMAP as well as the web interface.  

The best way to see how it works is to go to the Uncensored BBS:
[http://uncensored.citadel.org/](http://uncensored.citadel.org/)

Create an account and log in.  Of course, as a BBS user, you cannot see the private mailboxes, since you are not a mail user and don't have a mail account, but you'll get the idea.

Cheers,

Herman

---

### Post by Railsbuntu on 2008-03-05
Hi,

Does citadel allow anonymous smtp connection? I was not able to find how to set this up.

Because I am trying to use monit for monitoring my server and for reporting failures by email, but the current Ubuntu package of monit only supports unauthenticated smtp.

And for some unknown reason, email is suddenly not sent anymore (it used to work at one time) to the outside world anymore. It works on the LAN, but not through the internet, such as sending to gmail or other email providers. Anyone had this problem?

EDIT: one reason could by that my ISP is block my email, but why?

EDIT: sending mail using Windows XP built in smtp server has he same problems, impossible to get mail out of my network. Could it be my router that is blocking stuff? I don't think so.

---

### Post by Railsbuntu on 2008-03-06
One step further, I have opened my server to the internet. I have opened port 25, and I have tested it from dyndns port tool, it is accessible. I have a webserver running and it is accessible from outside the lan.

I tried sending an email from gmail to: someaccount@myipaddress

And in gmail I got the bounced following email:

> 
This is an automatically generated Delivery Status Notification

Delivery to the following recipient failed permanently:

    someaccount@myipaddress

Technical details of permanent failure:
PERM_FAILURE: SMTP Error (state 13): 551 5.7.1 <someaccount@myipaddress> - relaying denied

  ----- Original message -----

Received: by **10.150.150.3** with SMTP id x3mr2073693ybd.93.1204821655732;
       Thu, 06 Mar 2008 08:40:55 -0800 (PST)
Received: by **10.150.135.4** with HTTP; Thu, 6 Mar 2008 08:40:55 -0800 (PST)
Message-ID: <dcf510df0803060840h2410b3b4g96e722aff3fa9416@mail.gmail.com>
Date: Thu, 6 Mar 2008 17:40:55 +0100
From: "myaccount@gmail.com>
To: someaccount@myipaddress
Who the hell is the IP addresses in bold?

Does it mean the email never reached my server?

EDIT: I have now blocked port 25 in my router, and I have sent an email from gmail, let's see what happens.

EDIT: We are getting closer. I used Firebird to send an email. When port 25 is closed, firebird notifies that it cannot connect. So I open the port 25. Then the email is sent, but I wasn't asked for any login/password, and obviously I will never receive the email. What's happening?


EDIT: Holy crap!!! I have received some emails!!!! The problem is I haven't checked the inbox in between and don't remember the settings to make it work! :-P

There are also emails bouncing all around the place, it's getting crazy! But it has worked at least once!

EDIT: I tried sending a new email, but it bounced back to gmail. This was done with port 25 open in citadel.

EDIT: I opened port 587 in my router, and have sent email (yet to bounce/Arrive), I made a typo in my domain name, and it immedialtey bounced back. When the email address is correct it doesn't bounce back so quickly so some stuff is happening.

Are there eas to use tools for monitoring what's arriving on my server's ports?

---

### Post by wthanna on 2008-03-06
You might want to visit [https://uncensored.citadel.org/](https://uncensored.citadel.org/) which is where the support forum / bbs for Citadel is located.  You will find the developers of Citadel there. They are very helpful.

---

### Post by Railsbuntu on 2008-03-06
Hi,
How does it work? I have entered the support room, but do I simply enter a message in letter?

I was affraid to not be posting at the correct place.

---

### Post by wthanna on 2008-03-06
Simply go to [https://uncensored.citadel.org](https://uncensored.citadel.org) 
Enter your preferred username and password
Click "New User"
On the left hand side of the screen click "Rooms"
There is a "Room" or message board called "Citadel Support"
Post your questions there.

Have a great day!
Todd

---

### Post by HermanAB on 2008-03-07
You can monitor any connection with tcpdump:
$ sudo bash
# tcpdump -A -s 256 -i eth0 port 25

You can also use telnet to do a manual connection and use that to figure out what is going on.

---

### Post by Railsbuntu on 2008-03-07
Victory!

I used HermanAB's idea to send an email using telnet! Man I never thought I would use one day this prehistoric thing to debug such problem.

Incredible!

I simply had forgotten to define the domain name under the administration tab of citadel.

Cheers everyone, thank you very much for your support 
:popcorn:

EDIT: snatch! I don't seem to be able to send email to accounts such as gmail, yahoo, hotmail, etc.

---

### Post by Railsbuntu on 2008-03-07
Is there somewhere a decent citadel log file?

Because in /usr/local/citadel/data, it's full of unreadable junk, and it's pretty annoying to have to "sudo su" to cd in that directory.

EDIT: I have set a DMZ for my server in my router, just in case the packets were dropped at router level. But still no messages arriving, so the router is not the problem.

EDIT: by adding a keyword in the subject of a test email, and by searching the log file for that key word, I have found out that the emails are being bounced.

I see different error messages:

1) no route to host

and

2) Unable to connect to gsmtp147.google.com : 25

A solution could be that I need to set a  DNS MX Record to prevent from getting blacklisted by other servers.

---

### Post by Railsbuntu on 2008-03-07
After some investigation, I think I have no solution.

I am currently using a dynamic IP, and according to this forum post: [http://dyndnscommunity.com/forum/viewtopic.php?f=17&t=83&p=198]("http://dyndnscommunity.com/forum/viewtopic.php?f=17&t=83&p=198")

ISP could be blocking my email. Moreover I have used some online tools to check if my IP was blacklisted, and it is. However in the past, my citadel server has been able to deliver mail to gmail, so it is probably the IP that I am on now that is the problem, and I don't feel like connecting and disconnecting my DSL modem until I find a good IP.

My production server will be running on static IP, but in the mean time I cannot carry on my citadel tests as I don't know where the problem comes from exactly and I do not want to have a static IP for my home network.

---

### Post by artcancro on 2008-03-10
> **Railsbuntu said:**
> Is there somewhere a decent citadel log file?

Because in /usr/local/citadel/data, it's full of unreadable junk, and it's pretty annoying to have to "sudo su" to cd in that directory.

I think this question was asked and answered on the Citadel support forum, but just in case...

The ".log" files found in the /data directory are *not* syslogs.  They are database logs (journal files).  Their only purpose is to give the store layer a way to reconstruct your database after a hard crash -- for example, if the power to your server went out, or if someone decided to shut down Citadel using "kill -9 citserver" or something like that.  It's the same thing as a journaling filesystem.

To get Citadel to write log files, you have to tell it to.  The system administration manual lists the startup options that you can use to write to either stdout, a file, or syslog.  If you are doing trace/debug type of troubleshooting, turn up the log level all the way to 9 and watch it go.

---

### Post by Railsbuntu on 2008-03-10
Hi artcancro,

Thanks for your tip.

Now I have another problem. If I want to accept incoming mail from other servers such as gmail, yahoo, etc, I have to make available port 25 of citadel. 

But now anyone can connect to my citadel server on port 25 and send me spam email, I can restrict to only accept email for my domain, but still. Is there a way to only accept to send email from authenticated users?

---

### Post by Railsbuntu on 2008-03-11
I'm having a problem.

I can't access webcit using https when proxyied through nginx. I get the follwing error message: "No required SSL certificate was sent"

What could be going wrong? :confused:

EDIT: Fixed, I had to adapt the configuration file for citadel in nginx.

---

### Post by artcancro on 2008-03-13
> **Railsbuntu said:**
> But now anyone can connect to my citadel server on port 25 and send me spam email, I can restrict to only accept email for my domain, but still. Is there a way to only accept to send email from authenticated users?

Do not be afraid of opening port 25 to the world.

Citadel will not allow anonymous third party relaying.  In fact, it is practically impossible to configure Citadel to allow it.

Any mail arriving on port 25 without the SMTP client authenticating first, *must* be delivered to a user on your server.   Watch:

$ telnet uncensored.citadel.org 25
Trying 216.150.130.111...
Connected to uncensored.citadel.org.
Escape character is '^]'.
220 uncensored.citadel.org ESMTP Citadel server ready.
HELO spammer.com
250 Hello spammer.com (phantom.xand.com [216.150.131.207])
MAIL FROM:<spammer@spammer.com>
250 Sender ok
RCPT TO:<someone@yahoo.com>
551 <someone@yahoo.com> - relaying denied
QUIT
221 Goodbye...

---

### Post by Railsbuntu on 2008-03-14
> Any mail arriving on port 25 without the SMTP client authenticating first, *must* be delivered to a user on your server. 
Yes I know, unfortunately this means that anyone can spam/overload my server by sending emails to user accounts on the server. I don't know about the load of mail servers, but this means that potentially an attacker could crash my server by spamming the hell out of me, I could handle this at firewall level by refusing too many connections at the same time, but it's not that easy to implement.

---

### Post by Railsbuntu on 2008-03-29
Hi guys,

When I try to monitor Webcit with Monit, I am having problems. When I start/stop Webcit, the pid file doesn't get re-created, therefore now I can only stop webcit once. What's happening?

By the way the citadel mailing-list is almost impossible to follow, I had to remove my subscription, it was getting crazy. :(

EDIT: actually what happens, is that when I stop webcit while citadel is running, well webcit seems to be automatically restarted by citadel.

So I stop Citadel. Then I stop webcit. The CLI tells me that all went okay, but webcit.pid is still there whereas webcit-ssl.pid is gone. If I try to restart webcit, it tells me that it is okay for webcit but not for webcit-ssl. So I play a bit, then all pid files are gone, but webcit and webcit-ssl are accessible and work...

---

### Post by sineo on 2008-06-24
Hi...I have a similar problem with citadel. I can send emails fine...but when i try to send an email from gmail to a user on citadel, the email bounces back. If anyone has a solution for this, I would appreciate the help...Thanks.

---

### Post by Railsbuntu on 2008-07-11
> **sineo said:**
> Hi...I have a similar problem with citadel. I can send emails fine...but when i try to send an email from gmail to a user on citadel, the email bounces back. If anyone has a solution for this, I would appreciate the help...Thanks.

I'm a bit late, but it could still be helpful. Where is your citadel server running from? If you are at home, then it could be that your ISP is blocking your server from connecting to remote port 25. This is the case with my ISP, the only solution I have, is to pay for a static IP from my ISP, and then he will let me connect.

Otherwise it could be that your IP address is considered as spam. This seems to happen often with dynamic IP addresses, as some previous folks might have been spamming people.

---

