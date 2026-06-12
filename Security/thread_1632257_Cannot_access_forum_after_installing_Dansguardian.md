---
title: "Cannot access forum after installing Dansguardian"
date: 2010-11-27
forum: Security
---

### Post by nicho J on 2010-11-27
Hello,

I have just installed webcontent control following these instructions - 
**[SIZE=1][B][http://ubuntuforums.org/showthread.php?t=843510&#8207;]("http://ubuntuforums.org/showthread.php?t=843510%E2%80%8F")**[/SIZE][/B]

It has blocked the content that I wanted blocking but also when I try to access the ubuntuforum site, all I get it a white screen.

Please can you let me know what I need to adjust in the configuration so that I can access the forum with content control enabled.

Many thanks

Nicho

---

### Post by brian_p on 2010-11-27
> **nicho J said:**
> 

Please can you let me know what I need to adjust in the configuration so that I can access the forum with content control enabled.

Reverse all the steps you have taken, including purging dansguardian, Do you still get a white screen?

---

### Post by nicho J on 2010-11-27
All I have to do to stop the white screen is to turn the protection off. 

If I turn off the Firehol I can then access the forum without issue.

---

### Post by brian_p on 2010-11-27
> **nicho J said:**
> All I have to do to stop the white screen is to turn the protection off. 

If I turn off the Firehol I can then access the forum without issue.

Choice 1: Leave Firehol turned off.
Choice 2: Examine Firehol's rules for the cause of the problem.
Choice 3: Never read these forums again!

---

### Post by bodhi.zazen on 2010-11-28
> **nicho J said:**
> All I have to do to stop the white screen is to turn the protection off. 

If I turn off the Firehol I can then access the forum without issue.

If the problem is with Firehol, configure Firehol to allow the Ubuntu forums.

Dansguardian works w/ the forums.

I agree with your observation, running these tools takes some fine tuning.

Personally I use privoxy

[http://blog.bodhizazen.net/linux/web-content-filtering-made-easy/](http://blog.bodhizazen.net/linux/web-content-filtering-made-easy/)

---

### Post by nicho J on 2010-11-28
How do I go about checking the Firehol settings? I do not understand what the config file means or what I am looking for. 

We have found today that when we try to access [www.bbc.co.uk/cbeebies](www.bbc.co.uk/cbeebies) (childrens site which my son uses) the screen goes white for this aswell.

Obviously this means that at the moment we either have control that does not allow my son to access his website, or no control at all.

PLease help.

Thanks

---

### Post by brian_p on 2010-11-28
> **nicho J said:**
> 

How do I go about checking the Firehol settings? I do not understand what the config file means or what I am looking for.

The problem appears to be with Firehol but it could lie elsewhere. Anyway, we'll start with Firehol.

Find the file /etc/firehol/firehol.conf. The default content on installation is

```
# Accept all client traffic on any interface
interface any world
        client all accept

```

Does yours differ?

Also, what is the output of

```
sudo iptables -L
```

---

### Post by nicho J on 2010-11-28
The file /etc/firehol/firehol.conf. says:

# Accept all client traffic on any interface
interface any world
policy drop
protection strong
    client all accept
server cups accept

but the file open up as read only so I can't amend it. How do I open it to change it?

The iptables comes up with:
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         

Does this explain anything?

---

### Post by bodhi.zazen on 2010-11-28
> **nicho J said:**
> The file /etc/firehol/firehol.conf. says:

# Accept all client traffic on any interface
interface any world
policy drop
protection strong
    client all accept
server cups accept

but the file open up as read only so I can't amend it. How do I open it to change it?

The iptables comes up with:
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         

Does this explain anything?

You have to edit the file as root.

Try ```
gksu gedit
``` then open the file with gedit.

---

### Post by nicho J on 2010-11-28
I've tried to edit the config field but still no joy.

---

### Post by bodhi.zazen on 2010-11-28
> **nicho J said:**
> I've tried to edit the config field but still no joy.

Did you try the link I gave you to my Blog ?

That is how I personally configure Dansguardian.

---

### Post by brian_p on 2010-11-28
> **nicho J said:**
> 

Does this explain anything?

Well, the output of the iptables command indicates you have no filtering of outgoing requests, so accessing any website should not be a problem.

The firehol.conf is altered from the default but I don't think we need worry about that as the iptables ruleset is empty. Deleting or commenting out the extra lines wouldn't do any harm.

This doesn't seem to be a firehol problem. You mentioned stopping firehol. How did you do that? How did you restart it?

---

### Post by brian_p on 2010-11-28
> **brian_p said:**
> Well, the output of the iptables command indicates you have no filtering of outgoing requests, so accessing any website should not be a problem.

On reflection iptables -L is empty because you have firehol turned off. My conclusion is still the same though. What is in firehol.conf is not the cause of your problem.

---

