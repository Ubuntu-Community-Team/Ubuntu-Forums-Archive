---
title: "Setting up home server"
date: 2011-11-08
forum: Server Platforms
---

### Post by etienne@Rofti on 2011-11-08
Dear all

Since buying a laptop, my old desktop box is just sitting around gathering dust. Therefore, I decided that I should re-purpose it as a home server, installing Ubuntu Server. Being a bit of a n00b, I have found tutorials such as this one: [http://saturnlaboratories.co.za/blog/archive/2007/01/01/howto-ubuntu-home-lan-server](http://saturnlaboratories.co.za/blog/archive/2007/01/01/howto-ubuntu-home-lan-server) (...which was written by my own brother, so I have "free" access to support:))

Now, setting up a home server will be easy enough, as will be accessing it with SSH. However, the question I have is about access outside my house.

If, for instance, I were to set up some sort of database even website on it, how would I access it from OUTSIDE my home network? Could I, for instance, set up a website and have friends access it from elsewhere in the world? Would I even need a domain name?

If anyone has any access to tutorials, please let me know, as that will be the easiest.

---

### Post by thomasw_lrd on 2011-11-08
You're going to need a static ip address from you ISP.  If you're router/modem will support it, you can do port forwarding to use your dynamic ip address, but you'll have to check your ip everyday to see what it is.

---

### Post by rubylaser on 2011-11-08
> **thomasw_lrd said:**
> You're going to need a static ip address from you ISP.  If you're router/modem will support it, you can do port forwarding to use your dynamic ip address, but you'll have to check your ip everyday to see what it is.

Or, setup a free account with DynDNS or no-ip, and use one of their dynamic dns update clients, to automatically update a hostname with your dynamic public ip address.  Also, once this is in place, you're going to need to NAT that public ip to your webserver's private ip address.

---

### Post by ikt on 2011-11-08
static ip from isp + a modem/router which is capable of local loopback = painfree remote access.

The draytek 2820+ series are great for this sort of thing.

---

### Post by 1clue on 2011-11-08
Are you doing this just as an educational exercise or do you really need a server?  Seriously.

If it just sits there gathering dust right now, then it will almost certainly continue to do so after you put Ubuntu on it.  Especially if you're a n00b and you're installing a non-gui OS.

Put it on Craig's list, get a few bucks for it, and then go get a home office appliance.

Stick a hard drive on your wireless hub.  Mine allows a media server, file server and all sorts of features that I don't use but a normal household would.  You'll spend $100, you'll have something that's already set up for anything you want to do except a web server, and it will be both tiny and silent.

On the other hand, if you really want to experiment with server software as a major project, then ignore what I just said and go for it.

---

### Post by thomasw_lrd on 2011-11-08
> **rubylaser said:**
> Or, setup a free account with DynDNS or no-ip, and use one of their dynamic dns update clients, to automatically update a hostname with your dynamic public ip address.  Also, once this is in place, you're going to need to NAT that public ip to your webserver's private ip address.

That's an even better idea.  Didn't even think of it.  Will they register a hostname for you?  Or do you still need to do that?  I know I could look it up, but I'm lazy.

---

### Post by rubylaser on 2011-11-08
They have several domain names that you can add a free host to. For example, yourhost.bounceme.net.  This would not require you to purchase for a domain name.

---

### Post by JayKay3OOO on 2011-11-08
I'd not bother hosting your own website on your home server as if it gets a lot of traffic then it's going to chew your bandwidth up. Some companies may try to get you to purchase a business connection if you end up making anything out of it.

A NAS is probably better for file server tasks.

If you run Linux on your main box then you can easily run apache in the background on your laptop. Apache runs on Windows too.

If it's gathering dust then may I suggest you cover it up?

---

### Post by etienne@Rofti on 2011-11-11
Dear all

Thank you for the replies. Unfortunately, some of those giving replies forgot my question and suggested I NOT do what I intended. I appreciate your good intentions, but unfortunately that did not help with achieving what I am setting out to do.

However, to those who gave suggestions, the use of No-IP seems to be my best bet. Thanks to rubylaser for the suggestion. I will try that out.

---

### Post by rubylaser on 2011-11-11
No problem, glad to be of service.

---

### Post by Slim Odds on 2011-11-11
As was hinted at earlier, your terms of service may not allow you to run a web server on the Internet. You had better check into that first.

P.S. Your brothers blog could use an update, it's still suggesting downloading Dapper!

---

### Post by 1clue on 2011-11-11
> **etienne@Rofti said:**
> Dear all

Thank you for the replies. Unfortunately, some of those giving replies forgot my question and suggested I NOT do what I intended. I appreciate your good intentions, but unfortunately that did not help with achieving what I am setting out to do.

However, to those who gave suggestions, the use of No-IP seems to be my best bet. Thanks to rubylaser for the suggestion. I will try that out.

My questions weren't trying to get you to stop, I was seriously asking you to examine WHY you want to, and if some other approach wouldn't be better for you.

I've put together over a dozen "servers" from old hardware exactly the way you're describing.  At one point I had 3 at one time.  Then I realized those servers were more trouble than they were worth.

If you have the time and if your goal is to learn something more than it is to "make use of old hardware" then go right ahead.  If you have something specific in mind and a real reason to use that thing, then go ahead.

If, on the other hand, you're thinking of a media share for your iTunes, phones and whatever else then I personally think a SOHO appliance is smaller, quieter, incredibly more convenient, and above all, already set up for use by modern non-nerds.

---

