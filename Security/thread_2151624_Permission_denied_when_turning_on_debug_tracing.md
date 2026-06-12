---
title: "Permission denied when turning on debug tracing"
date: 2013-06-05
forum: Security
---

### Post by markling on 2013-06-05
I am unable to write to files in, or even go to, my debug or debug/tracing tracing directories.

$ sudo echo 1 > /sys/kernel/debug/tracing/tracing_on
bash: /sys/kernel/debug/tracing/tracing_on: Permission denied

$ sudo ls -l > /sys/kernel/debug/tracing/tracing_on
bash: /sys/kernel/debug/tracing/tracing_on: Permission denied

$ sudo cd /sys/kernel/debug/tracing/
sudo: cd: command not found

Also:

$ echo workqueue:workqueue_queue_work > /sys/kernel/debug/tracing/set_event
bash: /sys/kernel/debug/tracing/set_event: Permission denied

$ sudo echo workqueue:workqueue_queue_work > /sys/kernel/debug/tracing/set_event
bash: /sys/kernel/debug/tracing/set_event: Permission denied

This is frustrating because I have been trying to troubleshoot a serious performance issue. Various guides have led me to the point where I am trying these instructions:

[http://stackoverflow.com/questions/10846747/origin-of-a-kworker-thread](http://stackoverflow.com/questions/10846747/origin-of-a-kworker-thread)

[http://www.linuxforu.com/2010/11/kernel-tracing-with-ftrace-part-1/](http://www.linuxforu.com/2010/11/kernel-tracing-with-ftrace-part-1/)

---

### Post by SlugSlug on 2013-06-05
use 
sudo -s

then issue the commands without sudo

---

### Post by markling on 2013-06-05
Thank you, SlugSlug.

(I can see that "sudo -s" sets up a super user shell, but do you happen to know why this is necessary to access the debug directory?).

This has solved part of my problem. But I'm still hitting a wall. So, I can change directory to /sys/kernel/debug, where I could not before.

Yet:

# echo 1 > tracing_on
# cat tracing_on
0

The echo command refused me permission before. Now it sounds okay, but then seems not to have worked.

Similarly:

# echo workqueue:workqueue_queue_work > /sys/kernel/debug/tracing/set_event
# cat set_event
workqueue:workqueue_queue_work
# cat /sys/kernel/debug/tracing/trace_pipe > out.txt
bash: out.txt: Permission denied

So echo worked on set_event, where it did not work on tracing_on. But then I get permission denied when I try and get a trace feed output as a file.

This works on its own:

# cat /sys/kernel/debug/tracing/trace_pipe

It's creating a file that's causing the problem.

So:

# echo blah > blah.txt
bash: blah.txt: Permission denied

So I've got a super user shell so I can get into my debug directory. But I do not actually have all permissions when I get there.

I presume I'm missing something?

---

### Post by SlugSlug on 2013-06-05
whats output of 

```
ls -l /sys/kernel/debug
```

you can't 'sudo cd' probably due to sudo issuing a one off command as root so you need to be root to get to a dir but when your there your no longer root :/

---

### Post by markling on 2013-06-05
Now that sudo -s is open, ls -l /sys/kernel/debug works fine.

---

### Post by SlugSlug on 2013-06-05
try 
nano tracing_on


put your 1 in and save

---

### Post by markling on 2013-06-05
Same deal. nano text editor opens file okay. Edits okay: 0 changed to 1. Saves okay. But then:

# cat tracing_on
0

---

### Post by markling on 2013-06-06
I'm looking for a solution to this problem because an ugly performance problem has arisen on my computer. I am at a loss to troubleshoot it. Guidance online suggested a trace. The trace doesn't work because I don't have permission. Hence my request for help here in getting permissions in my tracing folder.

---

### Post by matt_symes on 2013-06-06
Hi

> **markling said:**
> I am unable to write to files in, or even go to, my debug or debug/tracing tracing directories.

$ sudo echo 1 > /sys/kernel/debug/tracing/tracing_on
bash: /sys/kernel/debug/tracing/tracing_on: Permission denied

<snip>

$ echo workqueue:workqueue_queue_work > /sys/kernel/debug/tracing/set_event
bash: /sys/kernel/debug/tracing/set_event: Permission denied

<snip>


You have to enter a root shell to enter these commands as suggested by SlugSlug.

The reason for this is because the sudo command is only working on the part of the command to the left of the redirection.

I.E. In this example

```
sudo echo 1 > /sys/kernel/debug/tracing/tracing_on
```

*echo 1* is running under elevated privileges, whereas the redirection to the file */sys/kernel/debug/tracing/tracing_on* is not and it's the redirection, or more accurately writing to the file, that requires the elevated privileges.

There are a number of ways to ensure that the redirection has the required elevated privilages such as entering a root shell.

```
sudo -i
```

...running the entire command under a temporary root shell.

```
sudo bash -c "echo 1 > /sys/kernel/debug/tracing/tracing_on"
```

...or ensurinig that writing to the file has the presquiste privileges for it to succeed.

```
echo 1 | sudo tee /sys/kernel/debug/tracing/tracing_on
```

> 
workqueue:workqueue_queue_work
# cat /sys/kernel/debug/tracing/trace_pipe > out.txt
bash: out.txt: Permission denied

This, i suspect, is failing because you are in a directory that you cannot create new files in.

```
root@matthew-S206:/sys/kernel/debug# pwd
/sys/kernel/debug
root@matthew-S206:/sys/kernel/debug# cat /sys/kernel/debug/tracing/trace_pipe > out.txt
-bash: out.txt: Permission denied
root@matthew-S206:/sys/kernel/debug# 

```

Try to create the file in your home directory.

```
cat /sys/kernel/debug/tracing/trace_pipe >  **~/out.txt**
```
```

root@matthew-S206:/sys/kernel/debug# cat /sys/kernel/debug/tracing/trace_pipe > ~/out.txt
^C
root@matthew-S206:/sys/kernel/debug# head -n3 ~/out.txt 
          <idle>-0     [000] d.s. 236969.439359: workqueue_queue_work: work struct=ffff880106c110e8 function=od_dbs_timer workqueue=ffff880101220540 req_cpu=0 cpu=0
          <idle>-0     [000] d.s. 236969.455352: workqueue_queue_work: work struct=ffff880106c110e8 function=od_dbs_timer workqueue=ffff880101220540 req_cpu=0 cpu=0
         firefox-4405  [000] d.s. 236969.463202: workqueue_queue_work: work struct=ffff880106c110e8 function=od_dbs_timer workqueue=ffff880101220540 req_cpu=0 cpu=0
root@matthew-S206:/sys/kernel/debug#
```

> # echo blah > blah.txt
bash: blah.txt: Permission denied

I.E You cannot create a new file under sysfs or under debugfs.

Kind regards

---

### Post by markling on 2013-06-07
A very helpful answer, matt_symes, thank you.

Curiously, when I went back to use your bash shell suggestion, I found that the tracing_on file was already set to 1. As you can see from above, it appeared not to have acknowledged the change I made. Then, a day later - perhaps after restart? - the change was found to be in effect. Your sudo clarifications have helped all the same.

---

