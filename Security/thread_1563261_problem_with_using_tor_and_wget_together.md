---
title: "problem with using tor and wget together"
date: 2010-08-28
forum: Security
---

### Post by claymore89 on 2010-08-28
Hi.

I am using wget through the tor network, and everything is working just fine. The only problem is that although I've configured wget to send a desired http referer, tor is blocking the referer (which is sent when wget is not working through tor). Is there any way to disable tor's referer blocking? 

Thanks. (I've tried /etc/torrc file, but can't find any workable configuration options.)

---

### Post by Agent ME on 2010-08-29
How exactly are you using wget through tor? And tor exit nodes shouldn't be messing with your traffic at all. Can you post the command you're trying to use so we can check if there's problems with it?

---

### Post by claymore89 on 2010-08-30
Yes.

Here is the relevant code:

    export http_proxy="http://127.0.0.1:8118"  #This sets up the proxy connection
    expect /home/pajach89/FARMS/bukisa/ipchange.txt  #This calls a file containing code that is in the next paragraph
    wget --page-requisites --referer=http://www.google.com --output-document=/home/pajach89/FARMS/bukisa/bukisadump.txt -U "$shuffinal" $final  ##$final is just the target site & $shuffinal is just a randomly chosen username
    export http_proxy=""  ##This closes proxy connection

the other code chunk (called by this line:  expect /home/pajach89/FARMS/bukisa/ipchange.txt ) is:

spawn telnet 127.0.0.1 9051
expect "Escape character is '^]'."
send "AUTHENTICATE\n"
expect "250 OK"
send "signal NEWNYM\n"
expect "250 OK"
send "quit\n"

and all this does is tell tor to build a new virtual circuit (so it switches the exit node and IP address when I want it to

(I configured the /etc/tor/torrc file to enable control port 9051 access: so there is a line in the configuration file that says:ControlPort 9051)

Ok. So, everything works great. Tor builds a new virtual circuit when I want it to, and the username occurs in wget as I've set it. The only problem is that I cannot get the referer to show, or any other headers besides the username when I check by loading a site such as "whatismyreferrer.com". 

When I don't connect to tor, wget sends the right specified http referer. I'm not sure what's going wrong when I use tor.

Thanks for your help.

---

### Post by cdenley on 2010-08-30
Tor isn't an HTTP proxy. Port 8118, is that privoxy? Your local HTTP proxy is what is removing the HTTP referrer, not tor. You can simply not use your HTTP proxy, and use only tor. I believe you just need to use a wrapper called something like "torify", "usewithtor", or "torsocks" when you run your wget command.

---

### Post by claymore89 on 2010-08-30
I'm sorry.

How would I use a wrapper exactly?

Can you give me an example of how to use one with the wget command.

Thank you.

---

### Post by claymore89 on 2010-08-30
Sorry for the dumb question. I got everything working. Thanks so much for your help.

---

### Post by bodhi.zazen on 2010-08-30
> **claymore89 said:**
> Sorry for the dumb question. I got everything working. Thanks so much for your help.

If you would take the time to post the solution for others using TOR that would be fantastic =)

---

### Post by d3v1150m471c on 2011-12-23
I do not know if this has been patched but wget with tor leaks dns queries. You might consider telnet or curl as an alternative.

---

