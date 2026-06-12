---
title: "cron not working ubuntu server 11.10"
date: 2012-03-31
forum: Server Platforms
---

### Post by test006 on 2012-03-31
Hi,
I am trying to setup a cron job that runs everyday to capture an audio stream from the internet using the rtmpdump tool.
This is what i have done:
```
[0 4 * * * /usr/bin/rtmpdump -n 1.1.1.1 -c 1940 --playpath Radio -r rtmp://1.1.1.1:1940/Radio -o /home/public/test 
```
I would like to start the rtmpdump to start capturing the audio stream every morning at 4am and output a file in the /home/public/ directory.
I have tried this as a root and normal user but i do not get any output in the output directory.
When i run the same line of command from the CLI it works fine without any issue. Can someone advise if i am doing anything wrong?

Please note IP address given is not real...it is just an example. 
How do i also view logs, i.e. any error messages that cron maybe gnerating. 

Thanks for your help.

---

### Post by josephmills on 2012-03-31
I am not the best cron person.but do you need to have a 0 brfore the 4 ? like 

00 04 * * * /usr/bin/rtmpdump -n 1.1.1.1 -c 1940 --playpath Radio -r rtmp://1.1.1.1:1940/Radio -o /home/public/test

You can read more about cron here
[https://help.ubuntu.com/community/CronHowto](https://help.ubuntu.com/community/CronHowto)

---

### Post by 2F4U on 2012-03-31
You will find a good documentation about cron here:

[https://help.ubuntu.com/community/CronHowto](https://help.ubuntu.com/community/CronHowto)

It contains a section about troubleshooting and where to find error messages.

---

### Post by WasMeHere on 2012-03-31
Hi test006,

I think you should remove the first character in the crontab entry
**[COLOR="Red"][[/COLOR]**

If that is not the problem (maybe only a typing error in the post), I suggest that you make some simple command, and make it repeat every minute:
```

# Minute  Hour  Day of Month  Month  Day of Week  Command 
    *       *        *          *         *       echo "Hello World">/tmp/hello.txt
```
I selected a command that should be portable and to write to a directory, that should be writable for everybody.

When this works for you, insert your real command. Remember that there might be problems because of the limited environment, so you may need to change permissions of [FONT="Courier New"][SIZE="3"]/home/public/test[/SIZE][/FONT]

---

### Post by bubylou on 2012-04-01
Delete [ and change 0 4 to 00 04. You also need to specify a path for crontab. You can do this by adding the following line to the top of crontab.

PATH=/usr/bin/rtmpdump

---

### Post by CharlesA on 2012-04-01
> **bubylou said:**
> Delete [ and change 0 4 to 00 04. You also need to specify a path for crontab. You can do this by adding the following line to the top of crontab.

PATH=/usr/bin/rtmpdump
This.

I've always throw any command I want cron to run into a script and tell cron to run the script instead of the actual command.

---

