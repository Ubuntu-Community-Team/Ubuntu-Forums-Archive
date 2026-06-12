---
title: "How to secure Ubuntu, Kubuntu, Xubuntu, etc."
date: 2008-07-24
forum: Security
---

### Post by SSVegito888 on 2008-07-24
I am new to linux and was wondering How to secure Ubuntu, Kubuntu, Xubuntu, etc.


Please give step by step instructions.


Also, I would like to enable wake on lan; but am not sure how to do this securely.



Thanks,

SSVegito888

---

### Post by scragar on 2008-07-24
There's not much security required, beyond what's default, you've got a passworded account, restricted access etc, only thing I can figure would make you more secure would be to go to the screen saver settings and making it lock the screen as well incase you have to leave the computer unatended. Hardy comes with a built in firewall, so there's no problems there...

@ other forum members: Anything I'm missing?

---

### Post by SSVegito888 on 2008-07-24
OK, I am in the process of waiting on another forum to find out which GUI for IP Tables is better.  It is between gufw and firestarter.

But, while I am here, what is the best GUI for IP Tables.


I am trying to transfer over from Windows so I still like to use GUIs.


I am also going to probably install openssh server with modem forwarded ports so I can access the server anywhere.


Any advice on securing the openssh?


Should I use a OS Hardening tool such as Harden or Bastille?

---

### Post by SSVegito888 on 2008-07-24
What exactly do you mean by restricted access?

---

### Post by hyper_ch on 2008-07-24
What do you want to secure against what?

There is no patent recipe for security ;)

---

### Post by SSVegito888 on 2008-07-24
I just want advanced general security.


Like to block vulnerabilities and other common stuff like hackers, bruteforce attacks, close unneeded ports,maybe malicious programs and scripts, buffer overflow attacks, etc.



Should I use a OS Hardening tool such as Harden or Bastille?


Thanks,

SSVegito888

---

### Post by hyper_ch on 2008-07-24
> **SSVegito888 said:**
> block vulnerabilities
Run the updates regurarly

> **SSVegito888 said:**
> bruteforce attacks
You can only brute-force if there are services listening

> **SSVegito888 said:**
> close unneeded ports
Make a default installation of ubuntu in a virtual machine, then from your host machine run nmap to check what ports are open...
Then make a default installation of windows and repeat the same...
Now tell me if any or both or just one of those systems needs to alter its firewall ;)

> **SSVegito888 said:**
> malicious programs and scripts
Don't install stuff from untrusted sources and for scripts audit them and don't just blindly copy'n'paste commands...

> **SSVegito888 said:**
> buffer overflow attacks
not sure what you can do on the end-user level against that except for running the lastest security patches for the programs installed...

> **SSVegito888 said:**
> Should I use a OS Hardening tool such as Harden or Bastille?
There's apparmor on Ubuntu

---

### Post by SSVegito888 on 2008-07-24
I don't think I have enough ram to use a virtual machine on my desktop because I only have 512 MB of ram.

As for Windows I am running vista ultimate on my laptop with 2 GB of ram.

so I don't know if I have enough ram on that computer or not either.


It has been a while since I used nmap.

I am planning on downloading nessus and all the plugins.

Can I use that instead?

I am about go to sleep pretty soon because I have a doctor's appointment later today and it is already 4:21 AM where I am in USA.




Thanks for all of your help. Your fingers can finnaly rest.


SSVegito888

---

### Post by hyper_ch on 2008-07-24
you should be able to run ubuntu and xp in a vm where the host has just 512 mb... it won't be very fast but it should run.

it's been years since I last used nessus... with nmap you just probe all ports on the target and check what ports are open or closed.

---

### Post by Archmage on 2008-07-24
> **SSVegito888 said:**
> I am also going to probably install openssh server with modem forwarded ports so I can access the server anywhere.

For this you should read some Howtows, because SSH is a serious thing than can easily open your whole system.

(Restricting user, different ports, baning, limiting ip-range and so on.)

---

### Post by Zack McCool on 2008-07-24
Are you not running a router/firewall?

Here is my results from nmap -PS localhost on a fresh install of Xubuntu Hardy:

```

Starting Nmap 4.53 ( http://insecure.org ) at 2008-07-24 04:37 EDT
Interesting ports on localhost (127.0.0.1):
Not shown: 1712 closed ports
PORT    STATE SERVICE
22/tcp  open  ssh
631/tcp open  ipp

```

Now, neither of those ports is being forwarded by my firewall, so they are safe.  If I didn't have a firewall running, I would do a couple of things.  First, if I wanted to have ssh open and running, I would figure out the IP ranges that I would want to be able to ssh from, then use ufw to block access to ssh from everywhere but those IP ranges.

I would also block 631 universally from outside IP's.  

The most effective method, though, is just getting a Linksys router WRT54G, and getting that set up right.  I prefer to use it with dd-wrt, but the stock firmware will do what you need just fine...

---

### Post by SSVegito888 on 2008-07-24
Right now I am not forwarding any ports through my modem. So am I safe?

---

### Post by SSVegito888 on 2008-07-24
When you say "I would also block 631 universally from outside IP's."


Do you mean you would block port 631 from coming in to your computer or do you mean you would block port 631 from leaving\going out from your computer?



Thanks,

SSVegito888

---

### Post by scragar on 2008-07-24
block it from everything other than the internal IPs(127.0.0.x if I remember correctly)

---

### Post by Krepta3000 on 2011-02-28
I've been hearing a lot of trash talk about how very insecure computers all over the world are, including Linux.  I like linux, I took a linux course in school.  I looked up OpenBSD and they claim it's vastly more secure than linux, apparently no matter what distro.  I just don't understand what makes it so totally secure, and linux not secure at all.  They even claim OpenBSD hasn't been hacked in 15 years or something!  Wow!

I want to know, how do I make my Ubuntu/Kubuntu as externally secure as I can without having to be a trained network security tech?  I do remember learning IPtables, in school, but I've forgotten a lot of stuff.
:confused:

---

