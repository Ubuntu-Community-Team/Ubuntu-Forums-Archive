---
title: "restart remote sshd in debug mode-- how under upstart?"
date: 2011-02-07
forum: Security
---

### Post by TopicMapper333 on 2011-02-07
Sometimes sshd (dpkg: openssh-server) is very persnickety and it must be debugged.  The new drill with upstart seems to make this very difficult to do on a remote machine.

The way that used to work:

/etc/init.d/ssh stop
/usr/sbin/sshd -d

(which ran sshd with debug output)

Now that sshd is handled by upstart,

/etc/init.d/ssh stop

does not stop sshd, or, if it does, sshd comes right back and occupies port 22, which is exactly what cannot happen if the config file or authorized_keys or whatever must be debugged.

Now, the beauty of "/etc/init.d/ssh stop" was that the existing ssh session -- the one I'm using to talk to the remote machine whose sshd behavior I'm trying to debug -- was unaffected.  But when I do

service ssh stop

I lose my connection to the machine, permanently.  Apparently existing ssh sessions are stopped, even though sshd itself has nothing to do with them any more.  Since the remote machine is in another city, it's not practical to go there and reboot it.  It's simply offline until some human being can go do something about it in person.

Does anybody know a way to stop sshd WITHOUT stopping existing ssh processes, under the new "service" (upstart) drill in 10.10?

---

### Post by cariboo on 2011-02-07
Wouldn't using:

```
sudo service ssh restart
```

also solve the problem, I know it doesn't answer your question, but I never have had a problem with ssh, so I never have had to restart the server while still connected.

---

### Post by CharlesA on 2011-02-07
I've had to restart sshd while still connected, and what cariboo posted will restart sshd without disconnecting you.

If you stop a service, it stops for everyone.

What are you trying to debug?

---

### Post by TopicMapper333 on 2011-02-07
I think you both misunderstand something.  Let me explain how sshd *used* to work (and I think it still does, really, and that maybe upstart just needs some minor refinement -- or maybe the refinement is already there but I haven't found the documentation).

My understanding, after quite a few years of using ssh, sshd, and writing applications around them, is that sshd just "answers the phone", waiting at one or more ports (port 22 by default) and then moving incoming authorized streams to other ports so that port 22 stays clear for the next incoming request.  Once moved to some other port, each ssh connection is independent of sshd; it's a completely distinct process.  That's why it *used* to be possible to stop sshd via 

/etc/init.d/ssh stop

on a remote server, while in an ssh session, without disconnecting yourself in the process.

This is no longer the case.  When logged into the remote server, it's true that I can (as root or via sudo):

service ssh stop

...but that disconnects me, and I'm *permanently* disconnected because there's no longer any sshd process there to "answer the phone" and reconnect me.

Now to your implied question: What goes wrong with sshd that has to be debugged in this peculiar way, i.e.

/usr/sbin/sshd -d

?  The answer usually, but not always, has something to do with file permissions and ownerships.  But which files?  Several directories and several files may be involved, and ssh is extremely persnickety about every aspect of everything to do with security, which is a very good thing.  The problem can also be in the config files for sshd.  Or in the login shell.  Or in the user's .ssh directory.  I've seen many kinds of problems, and I've been surprised many times.  The *only* way to find out what's bugging sshd is to put it into single-user, non-daemonic debug mode as shown above, and watch what it says.  

Of course, if you can't stay connected, it's not possible, having stopped the sshd daemon, to start /usr/sbin/sshd (as root or via sudo) with the -d option, and watch what it says while you try to log in from another terminal or whatever.  It used to be true that

/etc/init.d/ssh stop

would stop sshd and leave existing ssh processes -- ones that sshd has already shifted to other ports -- running.  Now, though,

service ssh stop  (as root, or "sudo service ssh stop" if you're not already root)

stops them all, dead.  You won't notice this unless you're actually using one of them at the time you stop the service.  

I see no good reason for upstart's "everybody must die now" treatment of all existing ssh processes, and I see very good reason to allow sshd to be stopped while leaving existing ssh processes running.  

I was thinking that maybe somebody on this forum knew.  [http://upstart.ubuntu.com](http://upstart.ubuntu.com) has nothing in it about ssh or sshd, at least not according to the search feature there.

I hope I've made it clear, now, exactly what the problem is.  

The ability to administer remote hosts' sshd configurations is not something I can live without.

What happens if I disable upstart?  Is there a way to do that?

---

### Post by CharlesA on 2011-02-07
> **TopicMapper333 said:**
> 
My understanding, after quite a few years of using ssh, sshd, and writing applications around them, is that sshd just "answers the phone", waiting at one or more ports (port 22 by default) and then moving incoming authorized streams to other ports so that port 22 stays clear for the next incoming request.  Once moved to some other port, each ssh connection is independent of sshd; it's a completely distinct process.

As far as I know sshd always listens on port 22 (unless you change it). Each connection has it's own process of sshd, but if you stop the sshd server, all services are stopped. That happens for any service, be it ssh, apache, mysql, anything. It's killed off since you told the machine to stop the service.

> Now to your implied question: What goes wrong with sshd that has to be debugged in this peculiar way, i.e.

/usr/sbin/sshd -d

?  

What are you having problems with specifically? Normally the configuration file is fine, and if you are using key logins, the permissions in ~/.ssh needs to be set a certain way for it to work.

---

### Post by TopicMapper333 on 2011-02-07
CharlesA,

You say, "...but if you stop the sshd server, all services are stopped".  Yes, that's exactly what I said.  And that's exactly what the problem is!  

Before the upstart-ification of sshd, we didn't have the problems that I've described in this thread.

You say, "...What are you having problems with specifically?"  I answered that question twice already.  Here are my answers, again:

(1) "Sometimes sshd (dpkg: openssh-server) is very persnickety and it must be debugged. "

(2) "The [problem that needs to be identified] usually, but not always, has something to do with file permissions and ownerships. But which files? Several directories and several files may be involved, and ssh is extremely persnickety about every aspect of everything to do with security, which is a very good thing. The problem can also be in the config files for sshd. Or in the login shell. Or in the user's .ssh directory. I've seen many kinds of problems, and I've been surprised many times. The *only* way to find out what's bugging sshd is to put it into single-user, non-daemonic debug mode as shown above, and watch what it says."

CharlesA, have you ever done any debugging in a situation in which you had thousands of possible places where the problem could be?  If so, you must know that in such a situation, there is no substitute for a report from the software (in this case, the sshd software) that can tell you exactly where the problem is.  The way upstart is set up now in 10.10, I can't get such a report from a remote machine.

So, the answer to your question, "...What are you having problems with specifically?" is: "I'm having problems getting a debug report from sshd running on a remote machine.  I can't get such a report now, because upstartification apparently denies me that ability."

Can you tell me how to get such a report, please?  Do I have to get rid of upstart in order to have the ability to debug sshd-mediated logins on remote machines?

---

### Post by cariboo on 2011-02-07
While connecting remotely via ssh, you can start a debug session using the following command:

```
sudo /usr/sbin/sshd -p 2222 -D -d -e
```

then connect from the client using port 2222, I just tried, it works for me.

---

### Post by CharlesA on 2011-02-07
> **TopicMapper333 said:**
> 
CharlesA, have you ever done any debugging in a situation in which you had thousands of possible places where the problem could be?  If so, you must know that in such a situation, there is no substitute for a report from the software (in this case, the sshd software) that can tell you exactly where the problem is.  The way upstart is set up now in 10.10, I can't get such a report from a remote machine.

The only things I've had problems with ssh were either a config setting in sshd_config or a problem with files in ~/.ssh

I don't recall if I've run into problems with different users or not.

Anyhow, try what cariboo posted, that'll get you a debugging session.

---

### Post by TopicMapper333 on 2011-02-07
Ah.  Good idea.

I'll have to punch a hole in the firewall for the test port, first, I guess, but that should work.

Many thanks!

I think I can adjust to the fact that 

service ssh stop

kills everything in sight.  It was very disconcerting, though, when I lost my connection altogether.  I wasn't expecting that.  It's quite different from the old behavior of 

/etc/init.d/ssh stop

.

I'm getting the idea that, under the "upstart" regime, there is NO WAY WHATSOEVER to stop sshd without stopping all existing sshd-mediated connections.  Is that correct?

---

### Post by CharlesA on 2011-02-07
That's correct as far as I know. If I am applying new config settings I just use this:

```
sudo service ssh restart
```

I don't think I've actually stopped SSH and then started it back up remotely. You might be able to do that by using screen and having it start ssh back up after it's stopped. I'm not sure tho.

---

