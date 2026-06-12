---
title: "thinclient will not login"
date: 2008-03-31
forum: Server Platforms
---

### Post by bitmonkeyagi on 2008-03-31
Ok.. I had previously posted some problems in another thread...but I"m going to try again, from a different angle.  Here's the trouble.  I installed Edubuntu server on my main comp.  it all looked good.  I did nothing to the system except to edit the /etc/ltsp/dhcpd.conf file to reflect my network name in the line " option domain-name "thinmonkey"; . I stopped there because some of the advice here seems a bit contradictory.  well...I did reinstall Wireshark too to take advantage of the info able to be gleaned from there.

I boot up the proposed thinclient comp, and it receives an address via dhcp, and it gives me an Edubuntu splash screen.  after a quick ctrl-alt-F1, I have a login cursor, to which I apply the only user I have on my server, "glennr".  I then enter the password.  the thinclient responds "login incorrect" and returns to allow another attempt.

So I fired up two things.  first, in terminal, I type:
tail -f /var/log/auth.log

and try to login on the thinclient again.  nothing shows up at all.  I exit out of the logfile, and open it again (you never know when someone will put a cookie back in the jar...) but still...nothing from the event of logging in.

So then I fire up wireshark, and I DO see activity.  Here's just a little bit of it, that I thought must be pertinent:

first line:
info: Authpriv.warning: login[3504] : pam_unix(login:auth): check pass; user unknown\n

So...where do I go from here?  what other info might be useful to someone trying to help me.  I'm desperate here!

---

### Post by bitmonkeyagi on 2008-03-31
Oh...one other detail.  eth0, which is the one serving the thinclient, is set to 192.168.0.254.  It seemed to me it should have been set to 192.168.0.1, based on the dhcp looking for that address by default, etc., but someone suggested it needed not to be.  which should it have been?

---

