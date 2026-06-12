---
title: "System log-level is too verbose at boot?"
date: 2021-03-24
forum: Server Platforms
---

### Post by tgp1994 on 2021-03-24
Ubuntu server 20.04.1 LTS

At some point, there was a change which caused system messages to be printed to the user's virtual console instead of remaining in the dedicated messages console. I have to run sudo dmesg -n 3 every time at boot to suppress these messages, when I never had to do that before. Does anyone know what changed, and if there's a configuration I can make to restore this back to normal?

Thanks!

---

### Post by LHammonds on 2021-03-26
I have not changed my log levels on my Ubuntu Server 20.04 LTS installation, here is my default settings (curious to know what yours is set to):

cat /proc/sys/kernel/printk
```
4       4       1       7
```

This means:
```

console_loglevel = 4
default_message_loglevel = 4
minimum_console_loglevel = 1
default_console_loglevel = 7

```

man dmesg
```

       -C, --clear
              Clear the ring buffer.

       -c, --read-clear
              Clear the ring buffer after first printing its contents.

       -n, --console-level level
              Set the level at which printing of messages is done to the  con&#8208;
              sole.   The level is a level number or abbreviation of the level
              name.  For all supported levels see the --help output.

              For example, -n 1 or -n  emerg  prevents  all  messages,  except
              emergency  (panic) messages, from appearing on the console.  All
              levels of messages are still  written  to  /proc/kmsg,  so  sys&#8208;
              logd(8)  can  still be used to control exactly where kernel mes&#8208;
              sages appear.  When the -n option is used, dmesg will not  print
              or clear the kernel ring buffer.

```

dmesg --help
```

Supported log levels (priorities):
   emerg - system is unusable
   alert - action must be taken immediately
    crit - critical conditions
     err - error conditions
    warn - warning conditions
  notice - normal but significant condition
    info - informational
   debug - debug-level messages

```

After changing the level, you might want to issue the dmesg command with the clear option.

```
dmesg -C
```

LHammonds

---

### Post by tgp1994 on 2021-03-27
My printk looks like: 7 4 1 7. Looks like my console_loglevel is in fact set too high. I wonder what's setting printk at boot?

Also maybe something of note: when I was rebooting to verify what printk is defaulting to, I noticed that my system boots up to display the messages console by default (VT7). I had no idea it was finished booting until I started seeing firewall messages being printed. I thought it would switch to a login prompt (i.e VT1) automatically, but I had to manually switch to login.

Thank you for your informative post!

---

### Post by tgp1994 on 2021-03-30
Update: I did a search through my /etc folder looking for all references to [FONT=Courier New]printk[/FONT], and I found a config file, /etc/sysctl.d/10-console-messages.conf from the package [procps]("https://packages.ubuntu.com/bionic/procps") with the line [FONT=Courier New]kernel.printk = 4 4 1 7[/FONT] which seems correct to me. So it's still a mystery how the loglevel is being set to 7.

---

