---
title: "Host and Hostname configuration issues"
date: 2008-05-02
forum: Server Platforms
---

### Post by R.Bucky on 2008-05-02
I need some serious help with my host and hostname files. I recently started hosting my web site using apache. I was messing around with the two files listed above, trying to get the mailserver to function properly and messed it all up. Basically, I am trying to get my mailserver and hostname/hosts files in order.

In terminal, when I type hostname, I receive this: 127.0.0.1 mark.buckyspalace.net mark

My hostname file is currently: 127.0.0.1 mark
                               127.0.0.1 localhost

While my hosts file is: 127.0.0.1 mark
                        127.0.0.1 localhost
                        127.0.0.1 localhost.localdomain localhost
                        192.168.1.1.0   mark.buckyspalace.net  mark

Messed up! My user name is "mark", web domain is [http://buckyspalace.net](http://buckyspalace.net).

Any ideas on correcting my jacked up files?

---

### Post by windependence on 2008-05-02
> **R.Bucky said:**
> I need some serious help with my host and hostname files. I recently started hosting my web site using apache. I was messing around with the two files listed above, trying to get the mailserver to function properly and messed it all up. Basically, I am trying to get my mailserver and hostname/hosts files in order.

In terminal, when I type hostname, I receive this: 127.0.0.1 mark.buckyspalace.net mark

My hostname file is currently: 127.0.0.1 mark
                               127.0.0.1 localhost

While my hosts file is: 127.0.0.1 mark
                        127.0.0.1 localhost
                        127.0.0.1 localhost.localdomain localhost
                        192.168.1.1.0   mark.buckyspalace.net  mark

Messed up! My user name is "mark", web domain is [http://buckyspalace.net](http://buckyspalace.net).

Any ideas on correcting my jacked up files?

The hostname is the name of your machine. The fully qualified domain name would be mark.buckysplace.net if your machine is named mark. This can be very important on a mail server.

Your hosts file contains local DNS entries, so that say you have a machine on your local network called becky, and it's IP address is 192.168.0.2 then if you put an entry in your hosts file like so:

192.168.0.2   becky.buckysplace.net   becky

Your machine will know that if you type ping becky, it will ping the IP address 192.168.0.2. It's just a local DNS entry.

You also need to set up your gateway and outside DNS settings so that your machine knows how to get out to the internet. can you access the internet with the server?

-Tim

---

### Post by R.Bucky on 2008-05-02
Hello. Yes, my server can access the internet and send emails. But, the mailserver takes approximately 1-2 minutes to send anything out. Also, terminal shows a completely different name than it used to. It used to read, "mark@bucky-desktop", and whenever I use a sudo command it returns "unknown host" but carries out the command.

---

### Post by windependence on 2008-05-02
> **R.Bucky said:**
> Hello. Yes, my server can access the internet and send emails. But, the mailserver takes approximately 1-2 minutes to send anything out. Also, terminal shows a completely different name than it used to. It used to read, "mark@bucky-desktop", and whenever I use a sudo command it returns "unknown host" but carries out the command.

If you changed the hostname, terminal will show user@hostname> for the prompt.

Can you post the contents of your hosts file again? Also tell me again what is returned when you type hostname and return in a terminal.

-Tim

---

### Post by R.Bucky on 2008-05-02
Here is my hostname file: 127.0.0.1 mark
                          127.0.0.1 localhost
                          127.0.0.1 mark.buckyspalace.net

Now, my server is busted. Nothing.

When I type in hostname, it is blank. Ugggg. 

Here is my hosts file: 127.0.0.1 mark
                       127.0.0.1 localhost
                       127.0.0.1 mark.buckyspalace.net  mark

I am thinking that my ip should go in here somewhere.

---

### Post by windependence on 2008-05-02
Let's try resetting your hostname.

Type in sudo hostname mark.buckyspalace.net at a prompt and press return. then type in hostname again and see if you get mark.buckyspalace.net

-Tim

---

### Post by R.Bucky on 2008-05-03
Yup, it changed to mark.buckyspalace.net. My server is still down. this is really frustrating. these hostnames are killing me.

---

### Post by windependence on 2008-05-03
> **R.Bucky said:**
> Yup, it changed to mark.buckyspalace.net. My server is still down. this is really frustrating. these hostnames are killing me.

What is listed in your httpd.conf file for the hostname? They must match. You should probably change it back to whatever it was before the change. That is most likely what is in the apache config file (httpd.conf). Note that changing the hostname with the hostname command will not survive a reboot. You will need to change your hostname and hosts files to reflect the change.

-Tim

---

### Post by R.Bucky on 2008-05-03
My httpd.conf says "buckyspalace.net. I changed my hosts and hostname files to match. Should they really have all of these names?

hostname:
127.0.0.1 mark
127.0.0.1 localhost
127.0.0.1 bucky-desktop
127.0.0.1 buckyspalace.net

hosts:
127.0.0.1 mark
127.0.0.1 localhost
127.0.0.1 bucky-desktop
24.18.97.15 buckyspalace.net mark

Thanks for sticking with this Tim! I REALLY appreciate it.

---

### Post by windependence on 2008-05-03
> **R.Bucky said:**
> My httpd.conf says "buckyspalace.net. I changed my hosts and hostname files to match. Should they really have all of these names?

hostname:
127.0.0.1 mark
127.0.0.1 localhost
127.0.0.1 bucky-desktop
127.0.0.1 buckyspalace.net

hosts:
127.0.0.1 mark
127.0.0.1 localhost
127.0.0.1 bucky-desktop
24.18.97.15 buckyspalace.net mark

Thanks for sticking with this Tim! I REALLY appreciate it.

You should only have one entry in the hostname file. That should be what the box is called and should be the FQDN. So, if the box is mark, then it should have one line that says:

127.0.0.1  mark.buckysplace.net

That's it. 

Now in the hosts file, you can have several aliases for the server if you want. 

127.0.0.1    localhost
127.0.0.1    mark.buckysplace.net   mark

This is all I would put in the hosts file for now. You could also include an alias for the local (internal) IP whatever that happens to be ex. 192.168.xx.xx or whatever your subnet is inside your network. Don't put your external address in there.

You will have to do a network restart after you are finished, better yet, try a reboot and then when you log back on, check and make sure your hostname command gives you whatever the hostname actually is.

I just looked at my config file and the only option I have is servername and that really doesn't matter, it's just what gets printed in the error messages. At any rate we need to fix your hostname and hosts files.

-Tim

---

### Post by R.Bucky on 2008-05-03
Hey man, you are a genious! Synaptic functions properly again and the sudo functions are correct and operational. My mailserver is fast as hell, but the mails are not being received by my gmail. I guess that is for another day. 

You saved my box from being slaughtered. Thanx man.

~Mark

---

### Post by ghostknife on 2008-05-03
If you have a dynamic IP gmail will reject the e-mails. For sending to gmail you can use a relayhost. If you have a dynamic IP it's better to always use a relayhost. 

Many people use blacklist services on their mailservers to reduce spam loads. Many of these blacklists lists any and all dynamic IP ranges. Meaning many servers don't accept mail from dynamic IPs.

An example of this is (and I recommend setting it up) spamhaus.org

---

### Post by windependence on 2008-05-04
> **R.Bucky said:**
> Hey man, you are a genious! Synaptic functions properly again and the sudo functions are correct and operational. My mailserver is fast as hell, but the mails are not being received by my gmail. I guess that is for another day. 

You saved my box from being slaughtered. Thanx man.

~Mark

Glad to help. I am happy you could get it going.

Ghostknife is right about what he says. Also, if you are going to run a mailserver you should set up reverse DNS for your static IP. many mailservers will reject mail that won't resolve to a real domain name.

-Tim

---

