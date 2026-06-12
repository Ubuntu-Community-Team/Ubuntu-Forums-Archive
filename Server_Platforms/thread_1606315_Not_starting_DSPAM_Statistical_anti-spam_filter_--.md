---
title: "Not starting DSPAM Statistical anti-spam filter -- disabled"
date: 2010-10-26
forum: Server Platforms
---

### Post by eric_1982 on 2010-10-26
I am trying to get dspam up and running on Ubuntu server 10.04 (LTS). I am running into an issue of starting dspam. when I run sudo /etc/init.d/dspam start I get the following error:

 Not starting DSPAM Statistical anti-spam filter -- disabled. 

I have installed dspam using apt-get and following the instructions on [http://2stech.ca/index.php/linuxtutorials/66-integrating-dspam-as-a-content-filter-in-postfix](http://2stech.ca/index.php/linuxtutorials/66-integrating-dspam-as-a-content-filter-in-postfix)

They mention that if I get that error that I need to turn it on under "/etc/default". I have looked at /etc/default/dspam and my config looks like this: 


# Do not start dspam.
START=Yes

# User that runs dspam.
USER=dspam

# Options for dspam.
#OPTIONS="--debug"

I am not sure what I am missing. Any one have any thoughts?

---

### Post by braverock on 2012-02-25
should be 

START=yes

The capital 'Y' won't work.

Regards,

  - Brian

---

