---
title: "Advise on a possible compromise"
date: 2011-09-28
forum: Security
---

### Post by dev100 on 2011-09-28
I have a server running obuntu that i leased so i can host my blog.
As soon as i got it, i went in and changed the passwords and looked at logs.

I saw thousands of brute force attacks. I then used Iptables and they got reduced but i can still see large # of trials.
Recently, i saw a rule in my iptables that bascially opened upb to ip. I didn't put that rule there and i'm the only admin.

I already run checkrootkit and it didn't find anyting.
So, if this is break in, i'm dealing with pretty skilled ones.

My questions: 

1.What can i do to find out for sure if this is compromised?

2. How can i check if logs are sanitized?
3. How can i check any other traces to?
4. Is there a way to tell if my commands are altered?

Also, is there way to remove services on /etc/services?
I only need ssh on the box. 

I appreciated your thoughts.

---

### Post by Dangertux on 2011-09-28
> **dev100 said:**
> I have a server running obuntu that i leased so i can host my blog.
As soon as i got it, i went in and changed the passwords and looked at logs.

I saw thousands of brute force attacks. I then used Iptables and they got reduced but i can still see large # of trials.
Recently, i saw a rule in my iptables that bascially opened upb to ip. I didn't put that rule there and i'm the only admin.

I already run checkrootkit and it didn't find anyting.
So, if this is break in, i'm dealing with pretty skilled ones.

My questions: 

1.What can i do to find out for sure if this is compromised?

2. How can i check if logs are sanitized?
3. How can i check any other traces to?
4. Is there a way to tell if my commands are altered?

Also, is there way to remove services on /etc/services?
I only need ssh on the box. 

I appreciated your thoughts.

Step 1 : Calm down :-)

Step 2 : Work through the problem logically. 

Brute force attacks against SSH are not uncommon, not even a little bit. First were you using a password to authenticate or keys? 

Now on to your questions :

1 -- If there is no evidence that is able to be found, you really have no way of knowing. A compromise could have occured for the purpose of "just to see if I can", they could and left it alone. This would be almost impossible to detect.

 2 -- The easiest way to determine if logs have been sanitized is to check for the following items

                - Large time spans with nothing occuring, IE : your time stamps are 2 hours apart.
                - EVERYTHING missing prior to a certain point
                - Repeated entries with changed time stamps, IE: someone copied and pasted an event over     
another one but kept the time stamp for the event covered up.
                - Replaced logs, log files from other systems that aren't yours.

3 -- Do you or your hosting service have an intrusion detection system? If so the logs from this may be able to help you. Also , you may wish to check for services running on the udp port that was opened. However, I really don't think that is a definite sign of a compromise, PARTICULARLY on managed hosting.

4 -- Check the checksums of the files against the actual version, dpkg can do this but rkhunter usually does as well. Also check ld.preload.so and your environment for changes.

As far as removing services first start by stopping the services

```

sudo /etc/init.d/servicename stop

```then 

```

sudo update-rc.d -f remove servicename 

```will remove it from starting on start up.

Out of curiousity what UDP port was opened?

EDIT : Also you may wish to install denyhosts or fail2ban to deter the bruteforce attacks, blocking them in iptables just bogs down your kernel

---

### Post by dev100 on 2011-09-29
Thanks for the good recommendations about the logs.
I was using password authentication and not keys at the time.
and the Udp is all not just one port. It opened all udp to particular ip address.
I have to see if there is way to send udp packets to the kernel which can probably by pass the rules i had for ssh/p 22.

About the services /etc/services is showing boat load and i need to find out more on how that works. Its been while since i did this and was doing more of APache work lately.
So, i'm doing catch up on lots of admin fronts.

Thanks

---

