---
title: "recieve txts?"
date: 2012-08-27
forum: Server Platforms
---

### Post by conradin on 2012-08-27
Hi all, 
lots of stuff requires texting now, and I am wondering if I can set-up a server that allows me to receive texts. Any good tutorials out there?

---

### Post by d4m1r on 2012-08-28
Do you mean connect your cell phone to your server to send/receive texts? You have to be more specific with what you are looking to do...

---

### Post by conradin on 2012-09-06
I mean:
I own no cell phone, but want to receive, and send texts, using my computer. Is that possible with standard consumer hardware?

---

### Post by LHammonds on 2012-09-06
I don't think you would be able to receive text messages on a computer.  The messages are sent over a phone carrier's network.

You can send an email to a text service "if" the carrier allows it.

For example, you could send an email to an AT&T customer by using a similar address but with their phone number instead of this example --> [email]8005551234@txt.att.net[/email]

LHammonds

---

### Post by iridium191 on 2012-09-06
We send SMS alerts from our network monitoring server using a 3G Cellular Network Router ([http://media.netcomm.com.au/public/assets/pdf_file/0010/40321/NTC-6908-Spec-Sheet-INT-web.pdf](http://media.netcomm.com.au/public/assets/pdf_file/0010/40321/NTC-6908-Spec-Sheet-INT-web.pdf)) - this model is a bit of overkill for that but it can also act as a backup internet connection. In our case it's basically a 3G router. Some mobile phones can also be used as modems. All it needs is a SIM card.
 
Do a search for "Extended AT commands" to see how to send and receive SMS from the command line or through a script, for example :[http://www.engineersgarage.com/tutorials/at-commands?page=2](http://www.engineersgarage.com/tutorials/at-commands?page=2)

---

### Post by sandyd on 2012-09-07
You can likely setup a SMPP server, but I do not know of one for Ubuntu.

---

