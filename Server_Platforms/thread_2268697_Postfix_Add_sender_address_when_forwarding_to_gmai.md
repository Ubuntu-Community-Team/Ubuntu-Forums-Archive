---
title: "Postfix: Add sender address when forwarding to gmail"
date: 2015-03-10
forum: Server Platforms
---

### Post by boast on 2015-03-10
Hi,

I would essentially wish to have my virtual_alias_maps file have something like so:

[email]Alice@web.com[/email] bob+${sender_name}@gmail.com

Since gmail forces the from address to be the same gmail account used for the relay, having the label tag in the forwarding address helps with labeling/filtering. 

So evereything intended to go to [email]alice@web.com[/email] is sent to [email]bob+viagraspam@gmail.com[/email] coming from [email]relayaaddress@gmail.com[/email]. 

TIA

---

