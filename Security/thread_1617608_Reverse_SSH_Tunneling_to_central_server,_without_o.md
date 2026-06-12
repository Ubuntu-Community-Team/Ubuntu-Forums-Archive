---
title: "Reverse SSH Tunneling to central server, without opening up cross-talk"
date: 2010-11-09
forum: Security
---

### Post by Jack_Simth on 2010-11-09
Hey all,

I've got a fun problem, please let me know if I've got the right forums.  Sorry for the wall-of-text, as well.

Due to business necessity, I've got a lot of Linux machines in the field that are all mirrored off of a master drive image.

Due to business necessity, they need to be root-accessible by SSH (although locked down by IP, so you pretty much have to be in my office or at the machine itself to make use of it - and if you don't have physical security, you don't have any security).

Due to business necessity, I occasionally have to hand out the root password for file system maintenance and initial setup, to individuals that are not totally trusted.

Now, the people setting these up in the field are not usually particularly technically inclined, and these machines need to be able to accept incoming requests.  What I'd like to be able to do, is tell the box dial home, and start accepting commands, so I can use the box as a relay to talk to the firewall, and set everything up myself.  

Now, of itself, [reverse SSH tunneling]("http://www.howtoforge.com/reverse-ssh-tunneling") is easy - I could do that, but I've got a problem: people not totally trusted sometimes end up with the default root password, and the default root password isn't always changed after installation, and I've got a lot of these boxes.  If I set myself up with a central server for reverse SSH tunneling, and set the boxes up to dial home on first field boot, the potential exists for someone who figures out how I'm doing this to start hijacking machines in the field by way of logging into the central server as one of them, and then using that center server to log into the field machines - the same way I'd be doing it to configure the hardware.

So I'm looking for people brighter than myself - any ideas?

---

### Post by P4man on 2010-11-09
Why couldnt you make a low privilege account on the server that the remote machines use to connect to via ssh? Basically that account only needs to allow someone to connect via SSH, setting up the tunnel but nothing else. Then you initiate the reverse tunnel from the server and log in as root on the remote machine.

---

### Post by Jack_Simth on 2010-11-09
Well, the only thing needed to do the cross-talk bit (however you want to term it), is ssh and the password for the other machine.  Can you permit logging in by SSH without permitting use of SSH?  How would I go about creating such a user?

---

### Post by tgm4883 on 2010-11-09
Not sure what the clients need to do on the server, but take a look at ssh authorized keys (specifically the command= section) [http://man.he.net/man5/authorized_keys](http://man.he.net/man5/authorized_keys)

This will make it so they cannot login to the central server, but could run a command on it (and only the command you specify)

---

### Post by P4man on 2010-11-09
Someone correct me if Im way off base here.
As I understand, with a reverse tunnel, you do two things.

1) your remote desktop connects to you server, logging in with an account that exists on that server and setting up a tunnel. For instance on the remote client would run something like:

```
ssh -R 5000:localhost:22 sshuser@yourserver
```

sshuser would be a low privileged user account on the server. 

2) From the server you just do:

```
ssh localhost -p 5000 root@client
```

And you will log in as root on the remote machine. You connect to localhost because all local traffic to port 5000 is forwarded via SSH through your reverse tunnel, back to port 22 on the remote machine.

---

### Post by Jack_Simth on 2010-11-09
> **tgm4883 said:**
> Not sure what the clients need to do on the server, but take a look at ssh authorized keys (specifically the command= section) [http://man.he.net/man5/authorized_keys](http://man.he.net/man5/authorized_keys)

This will make it so they cannot login to the central server, but could run a command on it (and only the command you specify)
The client doesn't need to do anything on the server - it just has to set up a tunnel back to the client (which an admin logged into the server then uses to set things up on the client's firewall - ideally with X11 forwarding, as most firewalls nowadays use a web interface).  Will it let me call... what would it be.... something like...

ssh -R [Port]:localhost:22 -i setup_id_file setup@[IP Address]



P4man: That's right... but then the question becomes: How do I prevent the low-privileged user from getting access to ssh (ever), as ssh is all that's needed to talk to another machine the same way?

Getting the clients to talk back to the center server isn't a problem.  Preventing a compromised client from compromising other clients is a problem.

---

### Post by P4man on 2010-11-09
> **Jack_Simth said:**
> 
P4man: That's right... but then the question becomes: How do I prevent the low-privileged user from getting access to ssh (ever), as ssh is all that's needed to talk to another machine the same way?

Im not sure I understand. ssh alone doesnt let you do anything, you need to have the user account credentials which you wouldnt have to give to anyone. You would at most compromise the login/password of the 'sshuser' on the server, just lock that account down that it cant do anything.

Since you make clones and I assume all clients have the same root password, you dont give that root password to your clients or do you? Without that password, they cant do anything to another client. Remember the sshuser is a user account on your server and nowhere else.

---

### Post by Jack_Simth on 2010-11-09
> **P4man said:**
> Im not sure I understand. ssh alone doesnt let you do anything, you need to have the user account credentials which you wouldnt have to give to anyone. You would at most compromise the login/password of the 'sshuser' on the server, just lock that account down that it cant do anything.

Since you make clones and I assume all clients have the same root password, you dont give that root password to your clients or do you? Without that password, they cant do anything to another client. Remember the sshuser is a user account on your server and nowhere else.
Sadly, we do have to hand out the root password on occasion.  Needs of the business - we can't afford a $75-200 service call (regional) to send a tech out every time one of these clones decides it needs disk maintenance - so we need to walk someone on-location through it.  Sadly, this requires the root password.  Even if we could afford to send a tech out every time, occasionally we need to stop hiring one of these people - they're not totally trusted, and the cloned root password could theoretically get out that way.  Theoretically, we could fly one of our trusted in-house people that can do this out there each time... all three of them.  Sadly, this would have to be all they do, and would cost a grand or more each time (airline, hotel, plus the person's time - these things are scattered all over the united states, and there's literally hundreds of them, and we hammer the hard drives rather heavily).  

At present, the boxes are locked down pretty tight - in order to connect to one of them to even attempt to log in, you either need to be physically at the machine, or you need to be at one of a very small number of IP's under our exclusive control.  So at present, it doesn't matter too much if that cloned root password ends up in the wrong hands - they either have to be on-location at the client machine they're cracking (in which case, that client is lost, root password or no - if you don't have physical security, you don't have any security), or they need to be in our HQ (in which case, we've already lost anyway, client root password or no).  If we set up 'normal' reverse SSH tunneling, that goes away - the server would need to be able to accept connections from anywhere, as the point of this is to be able to correct client networks that have gone wrong and need to be set up again.

Does that make sense?

---

### Post by tgm4883 on 2010-11-09
> **Jack_Simth said:**
> Sadly, we do have to hand out the root password on occasion.  Needs of the business - we can't afford a $75-200 service call (regional) to send a tech out every time one of these clones decides it needs disk maintenance - so we need to walk someone on-location through it.  Sadly, this requires the root password.  Even if we could afford to send a tech out every time, occasionally we need to stop hiring one of these people - they're not totally trusted, and the cloned root password could theoretically get out that way.  Theoretically, we could fly one of our trusted in-house people that can do this out there each time... all three of them.  Sadly, this would have to be all they do, and would cost a grand or more each time (airline, hotel, plus the person's time - these things are scattered all over the united states, and there's literally hundreds of them, and we hammer the hard drives rather heavily).  

At present, the boxes are locked down pretty tight - in order to connect to one of them to even attempt to log in, you either need to be physically at the machine, or you need to be at one of a very small number of IP's under our exclusive control.  So at present, it doesn't matter too much if that cloned root password ends up in the wrong hands - they either have to be on-location at the client machine they're cracking (in which case, that client is lost, root password or no - if you don't have physical security, you don't have any security), or they need to be in our HQ (in which case, we've already lost anyway, client root password or no).  If we set up 'normal' reverse SSH tunneling, that goes away - the server would need to be able to accept connections from anywhere, as the point of this is to be able to correct client networks that have gone wrong and need to be set up again.

Does that make sense?


Hmm. If thats the reason you have to hand out the root password, wouldn't something like [Gitso]("http://code.google.com/p/gitso/") make more sense (cross platform reverse VNC client)

---

### Post by P4man on 2010-11-09
I dont really understand why you wouldnt change the root password before shipping the machine, but I assume you will have your reasons.

That said, Im not sure how they could abuse this to connect to another client 

As I understand it, the client machine wouldnt accept incoming SSH requests, rather it would initiate the connection to your server upon your or the customer request, right? So you could firewall incoming ssh requests on the clients (only local ssh access is needed). 

So what can  an attacker do.. he could ssh into your server, log in as "sshuser" while you have a tunnel to the another one.  Lets assume he somehow knows or can find the IP of the other machine and the port you are using on the first client (it can be random after all) then I suppose he could in theory ssh locally (on the server) to log in to the machine with your universal root password.  Is that what you are thinking?

Using a random port and preventing sshuser from executing ssh (or anything really) on your server would pretty much close that possibility I think.  But I admit not being much of a hacker so perhaps im overlooking some options available to him.

---

### Post by Jack_Simth on 2010-11-10
> **tgm4883 said:**
> Hmm. If thats the reason you have to hand out the root password, wouldn't something like [Gitso]("http://code.google.com/p/gitso/") make more sense (cross platform reverse VNC client)

Now, see, this is part of the reason I go looking for people brighter than myself - they tend to have solutions for such things.  I'll make sure to give that a close look.  Know of any way to get it to trigger on a single button-press from a text-based login screen?  Also, can it handle a few dozen clients attempting to connect simultaneously?  We've got hundreds of these things in the field.  > **P4man said:**
> I dont really understand why you wouldnt change the root password before shipping the machine, but I assume you will have your reasons.
 Mostly a tracking problem.  There's hundreds of them, and anyone in the office might need root access to any of them at any time.  So we'd need unique passwords, a very large database for them, and some kind of tracking interface that lists them all off.  Throwing that all together is a lot trickier than setting up a single central server that sits there and waits for clients to connect.  So I'm looking for the easier solution before moving on to the harder ones... but I do need to keep it reasonably secure. > **P4man said:**
>  
That said, Im not sure how they could abuse this to connect to another client 

As I understand it, the client machine wouldnt accept incoming SSH requests, rather it would initiate the connection to your server upon your or the customer request, right? So you could firewall incoming ssh requests on the clients (only local ssh access is needed). 

So what can  an attacker do.. he could ssh into your server, log in as &quot;sshuser&quot; while you have a tunnel to the another one.  Lets assume he somehow knows or can find the IP of the other machine and the port you are using on the first client (it can be random after all) then I suppose he could in theory ssh locally (on the server) to log in to the machine with your universal root password.  Is that what you are thinking?
 Basically.  It's doable - did it in my initial tests. > **P4man said:**
>  
Using a random port and preventing sshuser from executing ssh (or anything really) on your server would pretty much close that possibility I think.  But I admit not being much of a hacker so perhaps im overlooking some options available to him.

  Sadly, scripting is easy - assuming a cracker gets ahold of a client with this installed (doable - when someone goes out of business, we don't always get the hardware back; funny thing, a lot of guys who forclose on and liquidate a business think they own everything there, regardless of specific agreements between the original business owner and third parties), he'll know the server's IP address, and can dig up the contact method.  It's a fairly simple matter to write up a script to try all ports from 1 to 999999 in sequence with a particular username and password, and issue a series of selected commands.  So yes, if you could walk me through how to make a user that can log in *and nothing else* (can't even execute SSH to get back out), that'd work OK for my purposes.

---

### Post by P4man on 2010-11-10
Ill experiment with an sshuser account in a bit, but meanwhile, why dont you create 2 user accounts with sudo prividges on those machines, one which you dont give to anyone you dont trust and one thats different for each machine and that you give to the customer if need be?

---

