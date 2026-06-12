---
title: "ufw  installed now what?"
date: 2011-04-02
forum: Security
---

### Post by lucubrate on 2011-04-02
:confused:Have installed ufw/gufw. All seems OK but I can't help thinking, now what?
I have just about mastered Archive manager and can now install prog's OK, so I know ufw in OK.
I know I have to be pro-active to maintain a secure system but dont know what to do with gufw in order to be pro-active?

---

### Post by marin123 on 2011-04-02
i thought you had ufw installed by default.

run this:
```
sudo ufw status
```

and see if the firewall is enabled and thats it.

you dont have to worry much about safety on ubuntu or any other linux. its safe by default :)

---

### Post by brian_p on 2011-04-02
> **lucubrate said:**
> :confused:Have installed ufw/gufw. All seems OK but I can't help thinking, now what?
I have just about mastered Archive manager and can now install prog's OK, so I know ufw in OK.
I know I have to be pro-active to maintain a secure system but dont know what to do with gufw in order to be pro-active?

Being pro-active implies knowing what the state of your machine is in at any time.

I imagine you have installed Ubuntu just recently. Suppose you were told this default install had no services running which would allow connections from the internet. In other words, nobody could access your machine. You might then think about whether you needed firewall rules to control what is already controlled and decide you need do nothing with ufw/gufw apart from remove them from the system.

---

### Post by bodhi.zazen on 2011-04-03
> **lucubrate said:**
> :confused:Have installed ufw/gufw. All seems OK but I can't help thinking, now what?
I have just about mastered Archive manager and can now install prog's OK, so I know ufw in OK.
I know I have to be pro-active to maintain a secure system but dont know what to do with gufw in order to be pro-active?

If you want to be proactive with security I suggest you read the security sticky.

Assuming you are running a desktop and are behind a router, activating your firewall does very little, if anything, to increase security.

---

### Post by cjsteele on 2011-04-03
> Assuming you are running a desktop and are behind a router, activating your firewall does very little, if anything, to increase security.

That is a naive mendacity.  

1) "routers" simply pass traffic between multiple subnets.  While a lot of "broadband routers" also perform NAT, you would be remiss to assume that all "routers" perform such packet mangling.

2) Not enabling your firewall in large networks, or public-private networks (e.g. coffee shops, airports, conference centers, etc.), is poor-form at best.  Just because you're not on "the internet", doesn't mean there aren't threats on the private network.

From my experience, you should always operate from a position of minimal trust (not to be confused with "maximum paranoia".)  That is, trust other people, computers and networks only in so much as you must to achieve your goals without overly cumbersome or unwieldy security measures.

Cheers,
-C

---

