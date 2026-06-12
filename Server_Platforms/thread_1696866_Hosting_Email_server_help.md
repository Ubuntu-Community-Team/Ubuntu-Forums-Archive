---
title: "Hosting Email server help"
date: 2011-02-28
forum: Server Platforms
---

### Post by kamgos on 2011-02-28
Hi 
I am planning to host a local email server
current I am using mdaemon 
My scenario is we are having 2 office at 2 different location

Layout
domain.com( host by third party we are using pop to download)

office 1 we use mdaemon :user1@domain.com

office 2 we use mdaemon :user2@domain.com

In both the offices i have forward all unknown mail to domain.com so user1 can receive mail from user2 and vice versa.

Currently i am using Ubuntu server 10.04 64 bit with squid working fine

I want get it done in postfix can any one tell me what are other application will be required to solve my purpose and how to get it done
Thanks in advance

---

### Post by lisati on 2011-02-28
Welcome to the forum.

Here's a short-ish answer, to start the ball rolling. I'm a bit distracted by TV and the need for a cup of coffee at the moment.

A guide to a basic installation of Postfix can be found [here]("https://help.ubuntu.com/community/Postfix").

The next step is figuring out getting the emails sent to the first domain to the domain you'll be managing with Postfix. At this point, there is more than one option.

The solution that comes to mind that is most like your current arrangement is to use the "fetchmail" program, which can use POP access to get email into Postfix.

Another option, which works best with a static IP and requires that port 25 isn't blocked, is to forward emails from your first host to your postfix installation.

---

