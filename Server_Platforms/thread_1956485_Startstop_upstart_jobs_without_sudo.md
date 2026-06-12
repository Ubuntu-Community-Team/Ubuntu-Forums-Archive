---
title: "Start/stop upstart jobs without sudo?"
date: 2012-04-11
forum: Server Platforms
---

### Post by Kethinov on 2012-04-11
I've got an upstart script called /etc/init/app.conf that looks like this:

```

description "app server"
author      "kethinov"

start on started mountall
stop on shutdown

# automatically respawn:
respawn
respawn limit 99 5

script
    export HOME="/var/www/app"
    chdir /var/www/app
    exec ./app >> /var/log/app.log 2>&1
end script

post-start script
    exec /root/bin/hoptoad.sh "app has started"
end script
```

Currently I have to use sudo to start and stop it, e.g. "sudo start app" or "sudo stop app" and whatnot.

Is it possible to enable select users or members of a specific group to start/stop jobs without sudo? I haven't yet figured out how to do that.

---

### Post by Lars Noodén on 2012-04-11
It's possible to allow a specific group to skip the password for certain programs. 

e.g.

```

%adm ALL=(ALL) NOPASSWD: /usr/bin/apt-get clean, /usr/bin/apt-get update, /usr/bin/apt-get upgrade, /usr/bin/apt-get dist-upgrade, /usr/bin/apt-get autoremove

```

See the manual page for [sudoers](http://manpages.ubuntu.com/manpages/oneiric/en/man5/sudoers.5.html) for the picky details.

---

### Post by Kethinov on 2012-04-11
Does that require those users to still have sudo? I'm hoping to grant users access to starting and stopping this service without granting them root privileges.

---

### Post by Lars Noodén on 2012-04-11
It allows root privilege, of the group 'adm', *only* for for running the programs listed and *only* with the parameters listed.  You could do it like this, assuming 'app' is the name of your startup script:

```

%adm ALL=(ALL) NOPASSWD: /sbin/start app, /sbin/stop app

```

That would allow anyone in the group 'adm' to run 'sudo start app' or 'sudo stop app' without a password but it would not allow anything else.  'sudo start ssh' or anything else would be forbidden unless specified elsewhere in [font=Courier New]/etc/sudoers[/font]

---

### Post by kevdog on 2012-04-11
To answer your question directly, I don't think ordinary users can run udev scripts individually -- an example of what you would want to do would be like individual users running their own cron daemon script.  Lars is suggesting you add yourself to a group that doesn't need a root password to run a specific command.  Its a workaround.

---

### Post by Kethinov on 2012-04-15
Thanks everyone for your help!

Lars, I used your sudoers NOPASSWD line and created a group for the app as you suggested. Works like a charm! :)

Thanks again everyone.

---

