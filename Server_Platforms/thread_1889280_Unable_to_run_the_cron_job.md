---
title: "Unable to run the cron job"
date: 2011-12-01
forum: Server Platforms
---

### Post by jeevandongre on 2011-12-01
have a AWS EC2 instance with ubuntu 10.10 server. I am trying to add a cron job to the list. But the cron job is not being executed.

I am actually uploading a particular file to aws s3 using s3cmd visit s3tools.org

What will be in the problem and also the solution.

Kindly help me out

Here is the bash script which has to be run

s3cmd put file-name s3://bucket_name/foder_name/file-name 
Here is the job

* * * * * bash /path/to/file.sh

---

### Post by Lars Noodén on 2011-12-01
What kind of errors is the log file showing?

```

grep CRON /var/log/syslog

```

---

### Post by jeevandongre on 2011-12-01
Hey thanks for reply. I checked the log it doesnt show any errors but I have added the log statements. have a look, but i am not able to upload the file.
CRON[29344]: (ubuntu) CMD (bash /home/ubuntu/upload.sh)

---

### Post by Lars Noodén on 2011-12-01
Does it work when you run the script manually?

---

### Post by jeevandongre on 2011-12-01
Yes the runs properly but when I assign the time it would not execute during that time.

---

### Post by Lars Noodén on 2011-12-01
There's a quirk with cron in that it needs to have an empty blank line below your configurations.  Is one there?

---

### Post by jeevandongre on 2011-12-01
Yes I do have empty blank line below the configurations.

---

### Post by Lars Noodén on 2011-12-01
Are you including the full path names for the programs in your script?  Alternately, set $PATH explicitly in the script. 

(Running out of guesses.)

---

### Post by jeevandongre on 2011-12-01
Yes I am including the full path names for the programs in my crontab.Its just a one line command which I am try to run why its taking so much time and giving me so much pain.

---

### Post by jeevandongre on 2011-12-01
@Lars Noodén Is there any alternative

---

### Post by jeevandongre on 2011-12-01
[LEFT][COLOR=#444444][FONT=Arial]I just observed the logs its actually executing the script but I am not able to see the results. I mean the files are not being uploaded to the S3[/FONT][/COLOR][COLOR=#444444][FONT=Arial] 
[/FONT][/COLOR][/LEFT]

---

### Post by Lars Noodén on 2011-12-01
Can you set the script to run s3cmd with the -v (--verbose) option?  That might help show where it's going wrong.

---

### Post by Habitual on 2011-12-01
Have you successfully used this s3cmd command before?
Who's running the script via crontab (or trying to?)
root or ubuntu or other (specify please).

I'm guessing here that you are trying to run this as the ubuntu user ("CRON[29344]: (ubuntu) CMD (bash /home/ubuntu/upload.sh)"

has 
```
s3cmd --config
```

been run as the user ubuntu?

This may help further...[https://forums.aws.amazon.com/thread.jspa?messageID=159290&#159290](https://forums.aws.amazon.com/thread.jspa?messageID=159290&#159290)

---

### Post by jeevandongre on 2011-12-02
I ran the script with -v. Its working fine. Did not show any error actually.

---

### Post by jeevandongre on 2011-12-02
It runs fine if I run the script as ubuntu it self.

---

