---
title: "Cant run official Ubuntu Ami's"
date: 2011-09-27
forum: Ubuntu Cloud and Juju
---

### Post by Gabriel Benmergui on 2011-09-27
Im following this tutorial: [https://help.ubuntu.com/community/EC2StartersGuide](https://help.ubuntu.com/community/EC2StartersGuide)

And i am not able to make the instance work. 

Tried both ami-06ad526f and ami-1aad5273

The instance is launched and shows the attached log, but i cant ssh, as it times out.I cant telnet it either.

Running the 'ec2-authorize default -p 22' command, after some maybe 15-20 minutes it says 
"
Unable to connect to host: 'https://ec2-xxxxx.compute-1.amazonaws.com'
"
Same with the command 
ec2-describe-instances

I created the instance both by AWS Management Console, and with the command suplied in that walkthrough (

ec2-run-instances ami-06ad526f --instance-type t1.micro --region us-east-1 --key ${EC2_KEYPAIR_US_EAST_1})

I have absolutely no feedback from the site or the command tools as to know what is going on. 

What can i do?

---

### Post by kim0 on 2011-09-28
So the ec2 cli tools are unable to reach Amazon? Perhaps there is a proxy on your network? try from a computer that's directly connected to the Internet

---

