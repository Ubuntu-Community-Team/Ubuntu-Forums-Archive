---
title: "How to know which firewall I am using ??"
date: 2007-02-20
forum: Ubuntu Christian Edition
---

### Post by glenn69 on 2007-02-20
I am using ubuntu CE v2.1.

I am having problems with a few online tasks.  I know very little about firewalls, etc, but from what I do know it appears that my firewall could be a possible culprit.

First, some of my problems:

- Counter Strike through cedega will not connect or display any game servers available.  The game will play, but wil not connect to any online servers.

- I use a Moodle site for some online classes and when I try to login, I receive an error message displaying that my cookies are not enabled.  (I do know that my cookies are enabled...that is not the issue)

How do I know which firewall is running on my machine?
Is it possible that I could have more than one running.  possibly as a result of adding one via something like Automatix?

I would like to know where to start looking for answers to my problems.  It's tough to find answers when I resaecrh because every bit of info that I learn points me to ten others that I must know first, and then those ten to ten others, and so on :(

---

### Post by mhancoc7 on 2007-02-21
> **glenn69 said:**
> I am using ubuntu CE v2.1.

I am having problems with a few online tasks.  I know very little about firewalls, etc, but from what I do know it appears that my firewall could be a possible culprit.

First, some of my problems:

- Counter Strike through cedega will not connect or display any game servers available.  The game will play, but wil not connect to any online servers.

- I use a Moodle site for some online classes and when I try to login, I receive an error message displaying that my cookies are not enabled.  (I do know that my cookies are enabled...that is not the issue)

How do I know which firewall is running on my machine?
Is it possible that I could have more than one running.  possibly as a result of adding one via something like Automatix?

I would like to know where to start looking for answers to my problems.  It's tough to find answers when I resaecrh because every bit of info that I learn points me to ten others that I must know first, and then those ten to ten others, and so on :(

If you are using Ubuntu CE then firehol is definitely running. I am not sure what you added with Automatix, but I know that firehol is needed for the Dansguardian filtering.

I don't know the answers to your problems, but I do know that firehol is running. I would suggest that you go into the Dansguardian GUI (System>Administration>Configure Parental Controls>and Disable the filtering. Then see if this fixes any of your issues. Then at least you will know that it is related to the filtering.

As far as getting answers you are in the right place. The Ubuntu Forums are very active and welcoming. The best bet is to Search first and then once you find yourself without an answer just ask. Be sure to give details and be specific. This will help since everyone's system is configured differently and everything matters.

God Bless, Jereme

---

### Post by glenn69 on 2007-02-21
OK, I disabled dansguardian and received the same error "cookies are not enabled".  I also bypassed dansguardian on port 3128 with the same results.  That seems to leave firehol as the last piece....right?

---

### Post by mhancoc7 on 2007-02-21
> **glenn69 said:**
> OK, I disabled dansguardian and received the same error "cookies are not enabled".  I also bypassed dansguardian on port 3128 with the same results.  That seems to leave firehol as the last piece....right?

That would be my assumption at this point. Maybe someone here that is more familiar with firehol can help with this.

Jereme

---

### Post by glenn69 on 2007-02-22
Appears that the problem is more likely tinyproxy.  Have read of others with similar problems.

How do I disable tinyproxy to test my hypothesis?

---

### Post by glenn69 on 2007-02-22
OK I found out how to stop tinyproxy.

/etc/init.d/tinyproxy stop

After doing that I logged in fine....well at least I know where the problem lies.........

Now, how do I allow the cookies with tinyproxy enabled ?

---

