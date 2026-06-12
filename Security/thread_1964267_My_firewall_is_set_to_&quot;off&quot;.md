---
title: "My firewall is set to &quot;off&quot;"
date: 2012-04-23
forum: Security
---

### Post by aligator12 on 2012-04-23
Should it be on? I remember messing around with it before, I can't remember if it should be on or off.

---

### Post by Dangertux on 2012-04-23
Depends on your usage. There are a number of tutorials on this forums as well as the rest of the internet for configuring strong firewall policies.

If you simply want a default drop all inbound policy you can do

```

sudo ufw enable

```

Hope this helps.

---

### Post by zdeuyo on 2012-04-23
Hello,

Your post does not specify which version of Ubuntu you are running. If you do a quick search in the Ubuntu software center for "Firewall" without quotes you should see a program with a blue and white shield pop up. Install it and turn it on. As the above member mentioned this is a very covered topic depending on your usage. If these answers solve your problem, please mark this as solved.

---

### Post by aligator12 on 2012-04-23
> **zdeuyo said:**
> Hello,

Your post does not specify which version of Ubuntu you are running. If you do a quick search in the Ubuntu software center for "Firewall" without quotes you should see a program with a blue and white shield pop up. Install it and turn it on. As the above member mentioned this is a very covered topic depending on your usage. If these answers solve your problem, please mark this as solved.
No, it does not answer my question. I use Ubuntu 11.10. My question is: is the default setting for the Ubuntu firewall "off"?

---

### Post by zdeuyo on 2012-04-23
> **aligator12 said:**
> No, it does not answer my question. I use Ubuntu 11.10. My question is: is the default setting for the Ubuntu firewall "off"?

It depends if you set it up that way when you were downloading updates. Also, the default is for Ubuntu's ports to be 'locked down' to prevent unauthorized access. The best way to know for sure is to enable it either through terminal as the user above mentioned or download the GUI (Graphical User Interface) program to help enable the firewall.

Please let me know if you have more questions.

---

### Post by aligator12 on 2012-04-23
> **zdeuyo said:**
> It depends if you set it up that way when you were downloading updates. Also, the default is for Ubuntu's ports to be 'locked down' to prevent unauthorized access. The best way to know for sure is to enable it either through terminal as the user above mentioned or download the GUI (Graphical User Interface) program to help enable the firewall.

Please let me know if you have more questions.
I don't remember if I turned it off or not. I am just going to go ahead and turn it on anyway. Will the firewall interfere with skype or virtual box connecting to the internet?

---

### Post by agillator on 2012-04-23
Aligator, I think you need to understand a little about firewalls. The common firewalls, including yours, are front ends for a program called iptables which is a tool for setting packet filters in the kernel. One way or another these packet filters are running all the time unless you are using a version of the kernel which has been compiled without it. You aren't. I say all this because it appears you think a firewall is like a light bulb - something you turn on or off. It isn't. 

That being said, what your question really amounts to is 'What packet filters are set, if any.' It is easier, but less accurate and in your case confusing to think 'on' or 'off'. Now, to answer your question, open a terminal and type 'sudo  iptables -L -v -n > rules'. When that has run and you have the prompt back, type 'less rules'. The first command lists the packet filter rules and the > rules puts them in a file named rules instead of displaying them on the screen. The 'less rules' then displays the rules file so you can read it at your leisure. Do not worry that you will not understand what it is telling you. That isn't important at this point. The first thing to look for are three lines: 'Chain INPUT (Policy . . .)', 'Chain FORWARD (Policy . . .)' and 'Chain OUTPUT (Policy . . .)'. The policies will be either ACCEPT or DROP. This means if no other rule is matched the packet will be accepted or dropped as indicated. 

Now, if all you have are the chain lines and the policies are all accept, everything in or out is accepted and passed to its destination. This is what most people mean by 'off'. But notice the firewall is actually doing something, it is NOT non-functioning. You may also find that there are only the three lines with no other rules and all policies are DROP. This means nothing goes in or out, period. The firewall is very definitely functioning. 

What the 'firewall' programs (ufw, etc.) do is set the policies and establish other rules for filtering packets. The bottom line for most simple firewalls is to let anything out and only let those packets in from connections that have originally been established from inside the firewall. From there on it gets more complicated and more technical. The front end programs (ufw, etc.) make it a lot easier to understand and do the grunt work for you. 

So, with that background, run ufw or its gui. It will tell you whether it is enabled or not. It it is not enabled, then there should probably be no rules except the policies and they should all be ACCEPT. If it is enabled, there should be some rules there that it puts automatically plus specific rules you ask it to put in. If you need to put in rules for skype or any program, the program documentation should tell you and/or the firewall front end you are using will offer you special rules for that program (ssh for example, or a web server, etc.) Running iptables directly is certainly more powerful, but also far more complicated and probably not something you want to do at this point. To see what I mean, in a terminal type 'man iptables'. I am sure you will not want to dig through all of that. 

So, knowing all of this, do as the others have suggested. Run ufw and see what it tells you. Hopefully it will make some sense to you now.

---

### Post by zdeuyo on 2012-04-23
> **aligator12 said:**
> I don't remember if I turned it off or not. I am just going to go ahead and turn it on anyway. Will the firewall interfere with skype or virtual box connecting to the internet?

The best way to find out is trial and error. Due to the nature of Ubuntu and various computers it can or can't. You can always add exceptions. Try it first. It does not effect me at all when I use those processes

---

### Post by aligator12 on 2012-04-24
> **zdeuyo said:**
> The best way to find out is trial and error. Due to the nature of Ubuntu and various computers it can or can't. You can always add exceptions. Try it first. It does not effect me at all when I use those processes
Well I turned it "on" and everything seems to work.

---

### Post by cariboo on 2012-04-24
To answer the op's question, seeing as nobody really did. In a default install ufw is disabled. you can check by using the following command:

```
sudo ufw status
```

If ufw is disabled, use the command that Dangertux gave in post #2 to enable it.

---

### Post by zdeuyo on 2012-04-24
> **cariboo907 said:**
> To answer the op's question, seeing as nobody really did. In a default install ufw is disabled. you can check by using the following command:

```
sudo ufw status
```

If ufw is disabled, use the command that Dangertux gave in post #2 to enable it.

Thank you for a solid answer admin

---

### Post by oklokl on 2012-04-24
sudo ufw enable
sudo update-rc.d -f ufw defaults
sudo ufw logging on
sudo ufw logging low

sudo nano /etc/ufw/before.rules

Please note ..
 COMMIT
 Should not write down.
If you write down will be disabled.

# ex> normalcy
-A ufw-before-input -p tcp --sport 70 --dport 90 -j DROP
COMMIT
On the basis of a sentence you do.


# ex> Bad error
COMMIT
-A ufw-before-input -p tcp --sport 70 --dport 90 -j DROP
ufw error..

---

