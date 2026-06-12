---
title: "SIMH startup script"
date: 2011-01-19
forum: Virtualisation
---

### Post by GarySm on 2011-01-19
For those struggling with a startup script (me) for their vax emulation.

Just place the startup file (myvax.conf) in the /etc/init directory as follows:
```

# When to start the service
start on (net-device-up
          and local-filesystems
          and runlevel [2345])

# When to stop the service
stop on runlevel [016]

# Automatically restart process if crashed
respawn

# Essentially lets upstart know the process will detach itself to the background
expect fork

# Start the process
exec /usr/bin/screen -L -S "MYVAX" -d -m -h 4000 /usr/local/vax/bin/vax

```

---

