---
title: "HTTPS, cannot accept certificate permanently"
date: 2010-10-01
forum: Server Platforms
---

### Post by HandleWithCare on 2010-10-01
Hi all! 
A few days ago I installed a new SVN server using ubuntu 10.04 server editiopn at our company and it runs almost flawlessly. *Almost* that is. The server uses a self-signed certificate so all communications go over https. 
The strange thing is this. When I run some svn command from my (windows) pc, like update I get asked whether or not I want to accept the certificate. Then I choose "accept permanently" end all goes well. In future command I don't get that question anymore. But when my colleague does the same from his pc, he also gets the same question. Now, when he chooses "accept *temporary*", all goes smooth. But when he chooses "accept *permanently*", like I did, he gets an error saying:
> 
RA layer request failed
svn: OPTIONS of 'https://path_to_some_repo': Could not read status line: An established connection was aborted by the software in your host machine.


Of course I googled my *** of on this and could find two things:
[LIST=1]
[*]Server settings are wrong
[*]there's something wrong with the firmware of the router
[/LIST]

The first couldn't almost be the case since it works for me and I followed the manuals.
The second one couldn't be it either because when I log in with my account on my colleague's pc, it works. This is also the case when he logs on to my pc.

So the problem exists specifically when he is logged in on his own pc. The setup of this machine is exactly the same as mine.

I am not a server expert (as you might have guessed :) ), so some help on this would be very much appreciated.

---

### Post by HandleWithCare on 2010-10-01
f me, it is fixed. Please tell me why so I can mark this solved, because it is still a mystery to me. What we did to "fix" this:
[LIST]
[*]clear the autentication data in tortoisesvn
[*]re-enter credentials
[*]it works
[*]strangely, it also works from eclipse and all other tools.
[/LIST]

But hey, it works! \\:D/

---

