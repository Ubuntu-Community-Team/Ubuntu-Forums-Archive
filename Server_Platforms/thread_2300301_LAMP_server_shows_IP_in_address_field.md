---
title: "LAMP server shows IP in address field"
date: 2015-10-24
forum: Server Platforms
---

### Post by Lokepi on 2015-10-24
Hello! I realise that this sort of thread has been made before, and I assure you that I have tried everything that have been posted on this subject that I could find using my google-fu. Though to no avail as I am still stumped :(.

My problem is as the title says that when I enter my domain name into my (or anyone else's) browser my website is displayed without any problems, however the domain name in the address bar is replaced with my IP address along with my port number for some god awful reason. 

As I am quite inexperienced when it comes to server management, I've no idea what to do now. These are all my settings that I figure could be useful: (The LAMP server is running on a local machine on my network)

[IMG]http://i.imgur.com/8bcWicB.png[/IMG]

---

### Post by SeijiSensei on 2015-10-25
I'm guessing it has something to do with the redirection.  Is your server at 162.256.119.253 which is where the A record points?  Or is it at 46.something?  With the little you gave us to go on, it appears that traffic to the first address is redirected to the second.  If the redirect points to an IP address rather than a hostname, then the IP address will appear in the browser.  If this is what's happening, why can't you put the server at the 162. address?  Or alternatively, point to the A record for the hostname to the 46. address?

Things work best when the hostname points directly to the address of the server that handles requests for that name.  Anything else is a kludge.

By the way, if you were to try and send me mail from anywhere inside registrar-servers.com, I'd never receive it because I block all email traffic from them.  Their servers are full of spammers. Before I blocked them I'd get dozens or hundreds of messages from machines named something.registrar-servers.com every day, none of which were legitimate.

---

### Post by Lokepi on 2015-10-25
Thanks for the answer, my server is on 46.xxx.etc, I have set up an A record on Namecheap, and I used mxtoolbox.com and entered a:myserver.com and it said that it points to that 162.256.119.253 adress, no idea what that is. I'd love to provide more info but I don't know what sort of info that would be useful to provide? As I said I'm very new to this thing, and it all seems like one big confusing maze. Do you think there's perhaps a problem with the A record?

EDIT: I'm also using Namecheap as the DNS service, as I have other domains there aswell. The domain name itself is not bought on Namecheap however as it is an .se adress.

IIRC I got the freedns1.registrar-servers.com and freedns1.registrar-servers.com from Namecheap and I entered those on the site where I bought the domain Name. 

All I want is to have my domain name point to my server, and having the name show up in the adress field :/

---

### Post by darkod on 2015-10-25
In you DNS manager (Namecheap according to you), modify the existing A record to 46.x.x.x. Don't use URL Redirect for @ as your screenshot shows. Same like you have www A record pointing to 46.x.x.x you need the same for the @ A record.

---

