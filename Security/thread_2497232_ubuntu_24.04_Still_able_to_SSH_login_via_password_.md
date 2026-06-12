---
title: "ubuntu 24.04 Still able to SSH login via password after PasswordAuthentication no"
date: 2024-04-27
forum: Security
---

### Post by p4rdner on 2024-04-27
I am running 24.04 server and I am trying to prohibit password logins. In /etc/ssh/sshd_config I set "PasswordAuthentication no" and restarted shh service (sudo systemctl restart ssh). I am still have to login via password. 

Just for tests, in /etc/ssh/sshd_config I set "PasswordAuthentication maybe" which gave me errors when I tried restarted shh service, so I know sshd_config is being read.

On my Debian machien there is a separate ssh and sshd service so I tried restarting/starting sshd
```
Failed to restart sshd.service: Unit sshd.service not found.
Failed to start sshd.service: Unit sshd.service not found.
```

I don't remember having this issue in 22.04, I've only had to set "PasswordAuthentication no" to disable ssh password logins.

Any help would be great, thank you
~Pard



EDIT: Well guess in order to solve my problems I first need to post about it. As soon as I posted I saw the 24.04 ships with /etc/ssh/sshd_config.d/50-cloud-init.conf    .... whish sets "PasswordAuthentication yes". Remove it and problem solved.

---

### Post by TheFu on 2024-04-27
If this is actually solved, please, please, use the **Thread Tools** button and mark it [COLOR="#FF0000"]**SOLVED**[/COLOR] to help people seeking answers find it faster.  At the same time, people coming to help don't waste their time.  

I'll likely hit this issue myself, so I do appreciate the cloud-init pointer.  More reasons to purge cloud-init from my systems and lock them from forced installs, if I needed more reasons.

---

### Post by ajgreeny on 2024-04-27
Interesting!

I wonder how many other changes to important filesystem sites that I often use have been made in 24.04.
One I do know already is that **/etc/apt/sources.list** is used no more; it is now a completely changed format file named **/etc/apt/sources.list.d/ubuntu.sources**

No doubt there will be many others that I just haven't yet found!

---

### Post by TheFu on 2024-04-27
> **ajgreeny said:**
> I wonder how many other changes to important filesystem sites that I often use have been made in 24.04!

There seem to be no end of 100% working solutions that cannot be tampered/screwed with because someone is confused that "change" is the same as "better".
Look at netplan.  It isn't any better. It just broke things that had already been working 20+ yrs and made it much more complex to manually setup AND to help others.

Same for systemd and nearly all the systemd-{insert complex, not-working-well tool} like resolvd or timed or mount or .... the list goes on.  Resolvconf was an early attempt at making something "better" that isn't actually better. Same for PulseAudio and network manager.  We already had **wicd** and **conman**, but someone wanted network manager for some reason.  BTW, I disable most things in this paragraph to avoid problems BEFORE they happen. Learned that when each of those listed items screwed up.

There's no replacement for experience and history.  When things change, there's often a really great reason.  Systemd was created to fix problems that I never had.  I miss the init.rc scripts. Those were easy to understand and get working.  Systemd Unit files can handle dependencies in a cleaner way, but I just saw yesterday that instead of looking for config files in /etc/, 3 more locations are going to be included. It will take about 6 months for those changes to make it into any releases.  I really miss the days of knowing that all configurations were in /etc/, in the place you expected to find them.  If you wanted something different, you had to go out of your way to create it, which was definitely possible, but no good sysadmin ever did.

Sigh.  Rant-off.  Sorry about that.  I'm not being fair. Haven't tried to install anything 24.04 yet. Might be a fantastic release and I may come to love it - or it could be like the Unity DE and upstart and all the other things that failed for assorted reasons.  Of all the issues, netplan is about the least hassle, but it is still a hassle.

---

### Post by currentshaft on 2024-05-07
a

---

