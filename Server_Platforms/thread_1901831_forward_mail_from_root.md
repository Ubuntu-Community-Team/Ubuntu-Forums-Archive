---
title: "forward mail from root"
date: 2011-12-29
forum: Server Platforms
---

### Post by fluca1978 on 2011-12-29
Hi,
I'm running a couple of servers that use postfix to deliver mails. The same is for the root account, that I don't want to receive any message (or better to receive them thru another acocunt). I've placed a MAILTO line in the beginning of my crontab, but this is not working. Any suggestion?

---

### Post by hwttdz on 2011-12-29
You can place in root's crontab "MAILTO=email_for_root@host.com" (it sounds like you might have put it in your own crontab?) or you can make a .forward file for root.

---

### Post by lisati on 2011-12-29
*Thread moved to **Server Platforms**.*

Postfix has some options you might want to look into. The easiest is probably setting up a mail alias, so that when mail arrives for "root", it gets sent to your regular admin account.

---

### Post by elico on 2011-12-29
i'm trying to understand what you want and still cant get it.
if you want to send the mails to another account then the local root use the alias file:
add to the file: /etc/aliases (and if not exist create it)
a line like this: 
root:   [email]destination_mbox@host.com[/email]

after that run the command: newaliases
to update the needed files on the os (so it will work)

it will tell the os\postfix that every email destined to root will go to the other account on other host.

---

### Post by fluca1978 on 2011-12-30
Thanks for the replies.
What if I don't want any message delivered to root?

---

### Post by SeijiSensei on 2011-12-30
> **fluca1978 said:**
> Thanks for the replies.
What if I don't want any message delivered to root?

If you mean you want all of root's mail to be forwarded somewhere else, use an alias as elico describes.  If you want all of root's mail to be sucked into a black hole and never be seen by anyone (a bad idea in my mind), you can alias the root account to /dev/null using the same method and replacing the forwarding address with "/dev/null".  Don't forget to run the "sudo newaliases" command after you've edited the /etc/aliases file.

---

