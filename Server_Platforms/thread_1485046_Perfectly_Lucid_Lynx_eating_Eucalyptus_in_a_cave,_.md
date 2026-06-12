---
title: "Perfectly Lucid Lynx eating Eucalyptus in a cave, grooving with Web Email DNS and FTP"
date: 2010-05-16
forum: Server Platforms
---

### Post by dbrooke on 2010-05-16
Sorry for the long title... couldn't resist
[http://tinyurl.com/39zxjv](http://tinyurl.com/39zxjv)

So, I want to install a modest but production Web hosting environment and co-locate the system somewhere. This will be my first *real* attempt at such venture. I've managed company hosting environments and played with personal hosting solutions. 
It's time to take it up a notch or two. ;-)

I thought I'd start this thread in case there were others that wanted to talk about the "**Perfect Economy Hosting Environment for less than 100 sites**".

Yes, I know there are services out there that can be attained for  pretty cheap... that is not for this thread. This thread is for the average small operation who wants to roll their own and who wants to make their best effort at competing with the big guys. ;-)

Services and client features aside for now, I think infrastructure and format is the first thing to talk about. Minus, standard features that any good colo facility would already have, I think some good *general* aspects of a hosting service would be:

1.) redundancy
  - power (mostly a service of the colo)
  - DNS perhaps
    multiple bind services on different networks/machines?
  - Email
    <same as DNS>

2.) Scalability and resource management
  - The big buzz word.. Cloud computing
    I noticed Ubuntu has a cloud enviro called "Eucalyptus"

3.) Process Isolation / Security
  - Virtual Machine hosting
    Takes care of both of these things in that, compared to a shared hosting environment, one neighborly site can't really interfere with another neighbor.

4.) Backup strategy and firewall.


With those general things in mind, I'm hoping to spark some good conversation that goes down to details.

First, **cloud computing** relating to Web Services and virtual machine hosting....

Is anyone using Eucalyptus currently? How is working for you guys?

I am familiar with VMware on the Mac Platform. I know many hosting companies now use VMware for a virtual machine hosting solution. My initial thought (without knowing much of anything about Eucalyptus) is that a VMware solution, coupled with Eucalyptus could be an interesting solution where both process isolation and scalability are covered. Any thoughts on that? Is there any other good solutions for process isolation/security? I really like solaris's "Zone" philosophy for this type of thing... not sure if linux has something similarly available.

Hardware, 
Upon suggestion, I am looking at the:
HP ProLiant DL100 line of servers.

Since I think it's best to run email and DNS and Web on separate machines/networks, I guess I would do something like the following:

server1 email and DNS
server2 redundant email and DNS
server3and4: cloud computing perhaps.

Those are my initial thoughts. I hope this turns out to be a thread with depth. I think a thread like this could really help out the Ubuntu server community.

Donovan

---

### Post by dbrooke on 2010-05-17
Maybe too much information??

Maybe I should start with the "Cloud vs. Traditional Shared Environment" discussion?

Advantages to the owner/admin that I see:
- Can charge more accurately/efficiently perhaps based on "utility billing" instead of "subscription billing".
- Resources are not necessarily limited to your hardware:

(Usuing UEC, it looks like you can create a hybrid local and public cloud type of setup. This gives you scalable resources that may also still meet security requirements)


Disadvantages to the owner/admin that I see:
- More complicated... troubleshooting, billing (you now have to create or find a billing resource that bills based on utility usage), and setup.
- ??


Advantages to the client: 
- I guess scalability perhaps.
- customer only pays for what they use (which can work out to either an advantage or disadvantage I guess)

Disadvantages to the client:
- May be longer for trouble resolutions (since it is a more complicated setup to troubleshoot)
- May be less performance due to overhead of cloud.


Once again, some initial thoughts. 

Donovan

---

### Post by dbrooke on 2010-05-21
Hmmm, no replies... this sure concerns me about going down the UEC route.

I've been on VMWare lately and do get some replies over there. They have a sort of private,public, and hybrid cloud solution and just announced some kind of deal with google. I don't think they are really compatible with Eucalyptus.

It appears to me however, they have a valid solution.. in that for a min. of $2K, one can get set up to have a cloud environment that contains a management app for VM's, apps etc.. along with perhaps a billing interface for utility based billing.

I haven't downloaded it so I only know what I read in a day or so.

Donovan

---

