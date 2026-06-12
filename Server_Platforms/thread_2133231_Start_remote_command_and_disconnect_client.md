---
title: "Start remote command and disconnect client"
date: 2013-04-07
forum: Server Platforms
---

### Post by mjitkop on 2013-04-07
Hello all,

since yesterday, I've been trying to start the execution of a command on my Ubuntu Server 12.04 from a client laptop (Ubuntu 10.04.) The connection is SSH.

I have no problem logging in to the server and executing commands from the terminal window on my client laptop. 
The problem I'm having is that when I disconnect and/or close my client terminal window, the command stops running on the server.

I have basic knowledge of Unix/Linux functionality and I know that you can run a command in the background using the '&' character at the end of the command line. I tried it but still, the command stops running on the server when I disconnect the client.

FYI, the server is in my basement and the command I want to run is HandBrakeCLI (with options on the command line). I also have Webmin installed on the server so I can monitor it in a browser (for example, check the running processes.)

HandBrakeCLI, for thoses who are not familiar with it, is used to encode video and that takes hours, sometimes overnight. Since my server is always running, I want to run the command on it and disconnect the client so that I don't have to leave my laptop on all the time.

Here are a few things that I have tried in my client terminal window:

```
1/ ssh -l basement <IP address>
2/ enter password
=> logged in to the server

3/ HandBrakeCLI <options> &
=> the command starts executing and displays stuff in the terminal window

4/ Check the running processes in Webmin:
=> HandBrakeCLI running (expected)

5/ Close the client terminal window

6/ Check the running processes in Webmin:
=> HandBrakeCLI no longer running

```
I also tried:

```
1/ ssh -l basement <IP address> 'HandbrakeCLI <options> &' 
2/ enter password

3/ check the running processes in Webmin:
=> HandBrakeCLI not running (not expected)
```

 
Since yesterday, I have tried several things and I have searched/read a lot of stuff on the internet but I haven't found the solution to my problem.

Does anybody have experience with this kind of thing? Who can help me with this task? 

Thank you in advance.

---

### Post by newboon2 on 2013-04-07
I'm fairly new to Ubuntu myself so I don't know if this carries over, but with bash on a Mac, I would use 'nohup' with '&', something like this:
```
nohup HandBrakeCLI <options> &
```

---

### Post by mjitkop on 2013-04-07
Thank you, newboon2.

I just tried it now and it seems to be working! I see that it created a file called nohup.out on the server and I'm not sure whether this is the actual output of the command itself or not. If that's the case, I can simply rename it later, no big deal.

Thanks again! \\:D/

I will wait until it's completely done and, if I got the result that I wanted, I will mark this thread as solved.

---

### Post by mjitkop on 2013-04-11
I realized later on that there is even a more elegant way for me to do this: schedule a command from the Webmin user interface. Indeed, there is a section on the Webmin UI that enables you to define a command that you want to run at a certain date and time on the server. It's all handled automatically by Webmin that schedules a job on the server. This way, there is no problem with a terminal window connected to the server via SSH. :guitar:

---

### Post by cariboo on 2013-04-11
Another way you run the command is to use screen. [Screen users manual]("http://www.gnu.org/software/screen/manual/screen.html")

---

### Post by mjitkop on 2013-04-11
Thanks, cariboo907. I will look into Screen in details. It's always good to have several options. :)

---

