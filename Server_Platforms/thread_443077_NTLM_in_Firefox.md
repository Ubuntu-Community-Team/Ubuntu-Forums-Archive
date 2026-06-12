---
title: "NTLM in Firefox"
date: 2007-05-14
forum: Server Platforms
---

### Post by Kryben on 2007-05-14
How do I set up a NTLM authentication in Firefox? 

The clients authenticate to the NT server using Winbind (+Samba). PAM has been set up to first use pam_winbind.so and then pam_unix.so, if that matters...

Is there something I have to do with Winbind, or Samba, or Firefox. Or do I need Squid or something else?
I really have no clue.

---

### Post by craigp84 on 2007-05-14
Hi Kryben,

I'm assuming you want authentication for web browsing through your server, in which case yes, you'll need to install something like squid too.

The NTLM in firefox "just works"(TM).

Get your proxy setup, configure winbind and you'll be laughing.

Hope this helps,

-c

---

### Post by Kryben on 2007-05-14
mmm, I don't really understand it.

Thus, the clients are Ubuntu systems that want to browse on the internet, yes. And there is a manual proxy configuration set too in Firefox. It asks for authentication when someones opens his Firefox.
Then also, there is an intranet website, listed in "no proxy for", but it ask for authentication as well because of policies set on that website. I've set the network.automatic-ntlm-auth.trusted-urls in Firefox to allow that one website.

The domain controller and the proxy server are both Windows system in a NT4 domain.

I suppose your answer will be the same :) but Squid is a server utility as far as I know, and I think it's risky to install it on clients ????

Greetings

---

### Post by craigp84 on 2007-05-14
Ah i misunderstood, i thought you wanted the ubuntu server as the proxy server, and windoze clients.

Well, it just got even easier :-) - in fact, it sounds like you already have it working. You will be prompted for a password when you start browsing the web with firefox on the ubuntu workstations, however this should only happen for the first site in each session, there's also an option to remember your username and password to save typing it in all the time!

There's no risk installing squid on a client workstation, it's just probably not all that worthwhile.

-c

---

