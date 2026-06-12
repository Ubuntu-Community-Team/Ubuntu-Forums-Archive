---
title: "Reconfigure squid3 via PHP"
date: 2009-02-12
forum: Server Platforms
---

### Post by Hightower666 on 2009-02-12
Hi all,

I have designed a web application that allows users to add sites to our whitelist. These are then added to a text file which squid3 uses to allow access.

Sites are added all the time and I need a way to restart/reconfigure squid3 via PHP (setup on the same server as Squid3).

I have tried squid3 -k reconfigure with shell_exec in PHP but I'm coming across all sorts of permission problems.

Is there a way for this to be allowed by the web user (not sure which account it is)?

---

### Post by conjur3r on 2009-02-12
The web user is www-data
You will need to configure the sudoers file to allow www-data to execute squid3 without a password.  Once done, simply add a sudo at the start of your shell_exec commandand then try again.

---

### Post by Hightower666 on 2009-02-12
Thank you!

Because I am a newbie at Ubuntu I didn't realise I still needed sudo before the command (because I thought the sudoers would take care of this).

I was so close before I posted - just needed the sudo at the start.

Anyhow, thats worked a treat - thanks!

---

