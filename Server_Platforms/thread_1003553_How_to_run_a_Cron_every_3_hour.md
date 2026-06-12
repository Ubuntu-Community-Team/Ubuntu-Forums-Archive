---
title: "How to run a Cron every 3 hour?"
date: 2008-12-06
forum: Server Platforms
---

### Post by lopes_andre on 2008-12-06
Hi,

I'm new to cron. I need to run a command every 3 hour. How I do that with Cron?

Something like this in the contrab -e file?

```

* */03 * * * comand

```

?

Best Regards, André.

---

### Post by vishzilla on 2008-12-06
thats correct

---

### Post by lopes_andre on 2008-12-06
Thks for you reply.

Best Regards

---

### Post by hrod beraht on 2008-12-06
> **lopes_andre said:**
> * */03 * * * comand

The first asterisk is for minutes and the * indicates any/all, i.e. run every minute. So if you only wanted it to run every three hours, set the minute at 0, or top of the hour.

```
0 */03 * * * comand
```

Bob

---

### Post by lopes_andre on 2008-12-06
Hi,

The crontab is not doing what I want... I explain:

I have edit my cron with the command "crontab -e" as root

I added the line:

```
* */03 * * * command
```

I think with this the Cron will run every 3 hour, but what I see in the /var/log/syslog is that after some time the command have started to run every minute.

My question, how the cron runs once every 3 hour?


Best Regards

---

### Post by lopes_andre on 2008-12-06
> **hrod beraht said:**
> The first asterisk is for minutes and the * indicates any/all, i.e. run every minute. So if you only wanted it to run every three hours, set the minute at 0, or top of the hour.

```
0 */03 * * * comand
```

Bob

I have not see your reply. Thanks for the solution.

Best Regards.

---

### Post by jmacx81 on 2008-12-06
what is cron?

---

### Post by spiderbatdad on 2008-12-06
> **jmacx81 said:**
> what is cron?

[https://lists.ubuntu.com/mailman/listinfo/Ubuntu-classroom](https://lists.ubuntu.com/mailman/listinfo/Ubuntu-classroom)
Your sig indicates you are looking for learning resources.
[https://help.ubuntu.com/community/CronHowto](https://help.ubuntu.com/community/CronHowto)

---

### Post by jmacx81 on 2008-12-06
> **spiderbatdad said:**
> [https://lists.ubuntu.com/mailman/listinfo/Ubuntu-classroom](https://lists.ubuntu.com/mailman/listinfo/Ubuntu-classroom)
Your sig indicates you are looking for learning resources.
[https://help.ubuntu.com/community/CronHowto](https://help.ubuntu.com/community/CronHowto)

thanks you very much. I'm actually glad you gave me resources instead of answers.

---

### Post by krishna5481 on 2008-12-19
You can also use 
* 0,3,6,9,12,15,18,21 * * * /your/command

Try this hard way, you might succeed. 

Regards,
Krishna.

---

### Post by Dr Small on 2008-12-19
If you want to run cron every three hours, you use:
```
00 */3 * * * command
```

This will ensure that it runs only once every 3 hours, and not every minute of that third hour.

---

