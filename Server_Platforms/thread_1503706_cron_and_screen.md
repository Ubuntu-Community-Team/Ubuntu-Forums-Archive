---
title: "cron and screen"
date: 2010-06-07
forum: Server Platforms
---

### Post by Hungry_Wolf on 2010-06-07
Hi all,

I'm trying to setup a cron with screen.

the purpose of running screen is because i want to resume to see the status of the job while it is running.

anyone can enlighten me how i should setup my cron.
I've tested with

00 14 * * * screen [command]

but the cron doesn't create a new screen.

---

### Post by Jakob Lundberg on 2010-06-07
Would it be enough to redirect the output to a file?
Then you can check the file to see the current status.

00 14 * * * [command] >> cronjob.log 2>&1

---

### Post by mobilediesel on 2010-06-07
> **Hungry_Wolf said:**
> Hi all,

I'm trying to setup a cron with screen.

the purpose of running screen is because i want to resume to see the status of the job while it is running.

anyone can enlighten me how i should setup my cron.
I've tested with

00 14 * * * screen [command]

but the cron doesn't create a new screen.

You're close. I also have a program run in screen via cron. Do it like this:
```
00 14 * * * screen -d -m [command]
```

---

### Post by Hungry_Wolf on 2010-06-07
> **mobilediesel said:**
> You're close. I also have a program run in screen via cron. Do it like this:
```
00 14 * * * screen -d -m [command]
```

thanks guy. it works. :)

---

### Post by mobilediesel on 2010-06-07
> **Hungry_Wolf said:**
> thanks guy. it works. :)

You're welcome!

Screen is so useful that you can't learn it all in a day. I'm sure I'm not yet using it to its full potential yet, either.

---

