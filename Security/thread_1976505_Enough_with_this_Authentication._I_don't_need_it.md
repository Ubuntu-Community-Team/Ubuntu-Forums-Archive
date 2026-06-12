---
title: "Enough with this Authentication. I don't need it"
date: 2012-05-08
forum: Security
---

### Post by Paul-Devon-UK on 2012-05-08
"WARNING Will Robinson - DANGER!" Etc.

I am an I.T. professional with over 25 years experience (started with CP/M before DOS was invented) so I do understand the risks.

I am trying Ubuntu 12.04 as a second O.S. It is a Sandbox, nothing more. I DO NOT CARE ABOOUT SECURITY on this machine. It is a sandbox.

As I am experimenting I am making constant changes and am getting to the point of uninstalling and giving up because of constantly being asked to tap in the same blasted password every few seconds.

I have done a little digging and came up with - run "sudo EDITOR=gedit visudo" and edit the file.

```
# User privilege specification
root	ALL=(ALL:ALL) ALL
me ALL=(ALL:ALL) ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL
me ALL=(ALL) NOPASSWD: ALL

# Allow members of group sudo to execute any command
%sudo	ALL=(ALL:ALL) ALL
me ALL=(ALL@ALL) NOPASSWD: ALL

# See sudoers(5) for more information on "#include" directives:

#includedir /etc/sudoers.d
me ALL=NOPASSWD: ALL
me ALL=NOPASSWD: /usr/bin/apt-get update
me ALL=NOPASSWD: /usr/bin/apt-get install *
```

Yes, 'me' is the user I chose as it is a Sandbox and I can't be bothered. Anyway, It does not work. I am STILL being pestered.

Before I delete the partition and go back to Windows, can anyone tell me what I did wrong?

---

### Post by uRock on 2012-05-08
The info you need is here. [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by Paul-Devon-UK on 2012-05-08
Thanks for the fast reply uRock. I will take a look when I am next back in Ubuntu.

---

### Post by CharlesA on 2012-05-08
The timeout period for ***sudo*** is 15 minutes, by the way.

Read the link uRock posted for more info.

It looks like you have it set up correctly, but you should remove these:

```
me ALL=(ALL@ALL) NOPASSWD: ALL
me ALL=NOPASSWD: ALL
me ALL=NOPASSWD: /usr/bin/apt-get update
me ALL=NOPASSWD: /usr/bin/apt-get install *
```

And just have:

```
me ALL=NOPASSWD: ALL
```

Note: This is not the recommended way to do it.

---

### Post by Hungry Man on 2012-05-08
EDIT: Nevermind.

---

