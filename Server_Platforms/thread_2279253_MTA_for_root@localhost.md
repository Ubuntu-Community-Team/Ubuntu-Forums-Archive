---
title: "MTA for root@localhost"
date: 2015-05-22
forum: Server Platforms
---

### Post by bruce-hyatt on 2015-05-22
I have a 14.04 server running and I need an MTA for messages from cron, etc., nothing else. Is something like Postfix really my only option? Looking at how to configure it I'm a little intimidated. Assuming that's the route I go, I have a few questions about the configuration:

- mydestination = MyServerName localhost?
- relayhost = localhost?
- I am the only user. Do I need to set up an aliases table? A database for the aliases table?!
- Can I read the emails with sudo vi /var/mail/username/whateverItWillBeCalled?
- This isn't likely to render the server non-functional while I work out the problems is it?

Thanks in advance.

- Bruce

---

### Post by bruce-hyatt on 2015-05-23
From the Postfix mailing list, to configure Postfix to deliver localhost email, in /etc/postfix/main.cf set:

myhostname = localhost.localdomain
mydestination = localhost localhost.localdomain

Once I get a chance to try it I will fill in any additional useful details.

- Bruce

---

### Post by cariboo on 2015-05-23
I'd suggest exim4, during installation it allows you to configure where you want mail sent, see attachment

The screenshot is actually Debian Jesse, but it works exactly the same in Ubuntu.

---

### Post by bruce-hyatt on 2015-05-26
It turned out to be easy. For anyone who might find it useful in the future, here's how I did it.

I installed Postfix:

```
sudo apt-get update
sudo apt-get install postfix
```

This starts a console menu-based installation where there's a selection for "local only." You'll see a screen asking for your FQDN (or fully-qualified domain name, I don't remember which). My computers host name was pre-filled in and I replaced that with "localhost.localdomain" (without the quotes). That took care of the syslog messages about no MTA.

Next I installed Alpine to read the emails:

```
sudo apt-get update
sudo apt-get install alpine
```

The next step was to start alpine as super user. I imagine it's important to do it this way so you'll receive email for root@localhost which is what you're after.

```
sudo alpine
```

That creates a folder for root@localhost accessible to your user. You just have to start alpine as super user.

The screenshot from Cariboo of the Exim4 installation looks like the Postfix installation screen so it's probably just as simple. The /etc/postfix/main.cf file has the hostname parameter as my computer's hostname, not localhost@localdomain as I was told by the Postfix mailing list it should be but it works perfectly so far.

- Bruce

---

