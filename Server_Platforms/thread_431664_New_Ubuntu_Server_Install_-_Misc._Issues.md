---
title: "New Ubuntu Server Install - Misc. Issues"
date: 2007-05-03
forum: Server Platforms
---

### Post by nomb on 2007-05-03
Hey guys,

I've never used ubuntu or a debian based distro before but I thought I would give it a try. 

I have my currently setup apache, ssh, and proftpd.  

My main problems are with apache.  For instance, I just went to my webpage ([www.nombyte.com](www.nombyte.com)) and it loaded with out any problems.  Then I went to another website and back to mine and now both firefox and IE say they can't find [www.nombyte.com](www.nombyte.com) or the ip address.  If I go to [www.network-tools.com](www.network-tools.com) I can do a look up successfully and also ping the server successfully.  I don't know how to fix this  or what the problem could be.

With ssh, I edited the ssh_config file and uncommented out the port option and set it to port 443 and opened that port in my firewall but it still times out and wont connect.

With proftpd, when I try to transfer something usually it will drop the transfer and just sit there.  I have port 21 and 20 open on the server.  Also this is within the local network.  I dont allow ftp to come in from the outside you have to ssh in and make a tunnel for ftp.

Thank you for your help.
nomb

---

### Post by nomb on 2007-05-03
And actually for apache it seems to be going in time spurts.  Example, If I reload it and it actually loads I have maybe 3 seconds to do things on it.  Then I must wait.  What is going on?

---

### Post by MJN on 2007-05-03
You really shouldn't be using port 443 for SSH as that's normally used for HTTPS.... Leave it at 22 or if you really want to change it do so to a port you're unlikely to be using (1024 or above at the very least).

Anyway, have you tried without any firewall running? If you're still in the 'learning' stages (aren't we all?!) then I'd suggest not tackling everything at once otherwise what you think might be an Apache problem may well turn out to be a firewall issue, and given you're having trouble with multiple services I'd initially suspect a common cause.

So, turn the firewall off and retry. Still no joy? If so, post your /var/log/apache2/ logs to see if they shed any light.

Mathew

---

### Post by nomb on 2007-05-03
Alrighty, I'll do that when I get home.  And the reason I am using port 443 is so I can connect to my server from work since they have almost everything blocked.
Quick Question - With Ubuntu how do you control services? 

When I tried to control ssh:

service sshd restart      - didn't work
service ssh restart        - didn't work
/etc/init.d/sshd restart - didn't work
/etc/init.d/ssh restart   - didn't work

(all those done as root)

---

### Post by MJN on 2007-05-03
Ah okay, I see. (As an aside it doesn't say much for their security if outbound traffic is controlled purely by port number and not traffic type, as you're demonstrating!)

Mathew

---

### Post by nomb on 2007-05-03
Sorry I think I edited the above post of mine while you were responding.

If it was a firewall issue though, wouldn't it be not working all the time and not sometimes?

I just read your response to my other post.  I don't actually have a script for ssh/iptables in /etc/init.d
Is there another package I'm suppose to install to get those?

---

### Post by MJN on 2007-05-03
Firstly, slow down!

Secondly, don't mix your posts up - you can't expect us to keep weaving between them! :)

To cut to the chase, to restart SSH simply run [B]sudo /etc/init.d/ssh restart

[/B]Regarding your firewall query iptables is powerful enough to do pretty much what you like with regards to when, why, and for how long, blocks should be in place and whilst I'm not suggesting you've 'accidentally' configured such a time-based ruleset let's just rule it out entirely by turning it off. (use **sudo iptables -F **to flush it of all rules - see [http://ubuntuforums.org/showthread.php?t=159661](http://ubuntuforums.org/showthread.php?t=159661) for details of creating your own /etc/init.d scripts for managing things a bit more elegently)

Just spotted you were talking about ssh_config - you should be editing sshd_config for your SSH server and if you haven't got that you haven't got an SSH server installed! (run **sudo apt-get install openssh-server** for this) If an SSH is not what you want, i.e. you just want a client, then don't change the port number in ssh_config - just specify at the end of the ssh command (e.g. ssh server.example.com 443)

Mathew

---

### Post by nomb on 2007-05-03
Sorry guess I am getting too excited.  

I don't have an ssh file in my /etc/init.d.

Also I will definately take a look at my iptables.  Once I can figure out how to control iptables by hand, since there isn't an iptables file in init.d either.

Would iptables make it randomly not work for a random amount of time?  If I was home I would have turned the firewall off by now but I was just curious.  This aspect is the only one which lead me away from iptables because I didnt think it could be so random.  

Maybe if you have a free second you can see if it loads and hit refresh a few times?

[www.nombyte.com](www.nombyte.com)

thanks for all your help matt.

---

### Post by MJN on 2007-05-03
I understand you're keen to get to the bottom of this one but trust me, it'll be a whole lot easier when you can sit in front of the machine and experiment!

I really wouldn't put too much effort into the how's and why's just yet - let's wait until you can turn iptables off (or rather remove the rules as mentioned) and then take it from there!

Mathew

(for what it's worth I can't access your site... yet! ;))

---

### Post by nomb on 2007-05-03
Ok, I will go ahead and turn iptables off at about 4:30ish.  Maybe then you can try again considering since I'll be on that machine there is no way for me to see if it is working.

---

### Post by nomb on 2007-05-03
Ok, I went ahead and got rid of firestarter.  I setup a rulse set allowing 80 so we'll see if that helps any. 

Few things though.  I've tried taking 113 out of his rule script, ive tried changin sport to dport (what is the diff?) and I've tried commenting out that line completely.  No matter what I do, it says that port is closed and not stealth.  What can I do about this?  

Thanks, 

nomb

ps. let me know if my site works.

Oh, and I still can't get ssh working.

---

### Post by MJN on 2007-05-03
I said get rid of the firewall! Keeping it in at this early stage is just asking for unnecessary headaches.

However, your site is visible at the time of writing so I guess you're good to go. What's wrong with SSH? What is it you're trying to do?

Mathew

---

### Post by nomb on 2007-05-03
Im trying to configure ssh.  I always do:

Port 443
Compression yes
PermitRootLogin no

but when I change the ssh_config file and then add the PermitRootLogin line it 1) errors on that line, and 2) even thought I restarted the computer and disabled the firewall it says that connection is refused on both port 22 and 443.

---

### Post by MJN on 2007-05-03
As I mentioned above ssh_config is the config file for the SSH **client**! If you're wanting to configure an SSH server then first, of course, you have to install it (as mentioned above also!), and second you then edit /etc/ssh/sshd_config (err.. also mentioned!).

Mathew

---

### Post by nomb on 2007-05-03
I apologize somehow i missed the sshd part.

It is installed now and everytime I try to start it, it says fail.  I tried looking in dmesg and messages for some error but I can't find one.  Any suggestions?

Thanks again,
nomb

---

### Post by MJN on 2007-05-03
Post the actual output (or does it literally just say 'fail'?). The logfile /var/log/auth.log may also detail what's wrong.

Does it work with the default config? If so, (and it ought to) make one change at a time and see what causes the failure. You really need to get into the habit of taking things one step at a time - jumping in with both feet will get you into a right mess!! ;)

Mathew

---

### Post by nomb on 2007-05-03
Ok trying with the default conf file:

  *  Starting OpenBSD Secure Shell server...                                                    [COLOR="Red"][fail][/COLOR]

unfortunately that is all it says.

---

### Post by MJN on 2007-05-04
And /var/log/auth.log says nothing?
 
You are prefixing the /etc/init.d/ssh command with sudo? (you need SU privileges to control the SSH server)
 
Mathew

---

### Post by nomb on 2007-05-04
Correct the auth.log says nothing.  And I am indeed using sudo.

nomb

---

