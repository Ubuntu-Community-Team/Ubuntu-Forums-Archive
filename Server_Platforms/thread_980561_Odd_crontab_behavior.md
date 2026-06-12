---
title: "Odd crontab behavior"
date: 2008-11-12
forum: Server Platforms
---

### Post by masaka on 2008-11-12
This problem has been driving me crazy for over a week now, so I'm desperately hoping someone can help.

I have a python script that downloads new files off of a server daily, analyzes it and adds the details of the files to a MySQL database. 

It works as it should under Terminal, over SSH, and even manually using the "Run now" button in Webmin's cron page. But when the job executes at the time specified in cron list, it runs as it should for a few minutes, and then it just stops. The process is still active but no work is being done. The output is truncated at where I assume the script stops. This is the line I use to execute the script:

```
30 20 * * * /var/www/Backup/grab.py | tee /tmp/output.log
``` 

I usually end up killing the process and running the script manually. Seeing as it runs perfectly fine under everything except when executed by crontab, I think the script itself is fine. It runs under a normal user account, but same problems under root. Permissions are correct. Restarted cron. I've run out of things to check!

If anyone has any ideas, I would be very glad to try them.

---

### Post by hictio on 2008-11-12
Here are a couple of things that helped me on situations like this in the past, perhaps they might be useful.

- Are you sure there is not an environment variable that you need to run the script? And you have to declare to the Python script, for instance.

- Try adding the full path to each of the executables the cron is using (python, tee)

- Do you need 'tee'? Can't you just '>' the output?

- Place all the commands on the cron line on a shell script, and invoke the script on the cron, instead of the commands.
Remember to make the shell script executable :)

---

### Post by masaka on 2008-11-13
It was the tee that was causing the problem. You've saved me hours more of headaches. Thanks!

---

### Post by hictio on 2008-11-13
Thats cool :D
Usually, if I don't want or need the output, I just redirect that to /dev/null.
But that was the first time I have seen using tee on a cron entry :)

---

