---
title: "Cron job doesn't run without root"
date: 2010-02-10
forum: Server Platforms
---

### Post by Windows95 on 2010-02-10
As the title says I am unable to run my cron tab job without root password.

```
@reboot /opt/liferay/liferay/tomcat/bin/startup.sh
```I made a little research on the forums and appearantly it should be changed as following:

```
getent passwd root
@reboot /opt/liferay/liferay/tomcat/bin/startup.sh
```Must I change "passwd" part with my root password?

p.s: please correct if I'm mistaken.

Thanks in advance :)

---

### Post by Windows95 on 2010-02-10
must  I also add 
```
chmod +x *.sh
```to my cron job?

---

### Post by cdenley on 2010-02-10
How/where are you creating the cron job? Everything but a non-root user's crontab will run as root. You don't need a password for it to execute.

```

getent passwd root

```
This is a command which lists details of the root user. It would accomplish nothing but break your crontab.

Of course any script you expect to execute as root must be executable by root.
```

sudo chown root /opt/liferay/liferay/tomcat/bin/startup.sh
sudo chmod 700 /opt/liferay/liferay/tomcat/bin/startup.sh

```

---

### Post by Windows95 on 2010-02-11
Sorry if I'm giving so little information to be helped on.I'm trying to run the app on a very similar linux distro called "Pardus".What I did was I typed **sudo su -** on console,gained root privilages by typing password then typed **crontab -e** ,after that typed in **@reboot...** part saved it under /etc/cron.d/ folder and when I restart my pc the hard disk activity light on the case goes up as if it's running but when I type **[http://localhost:8080](http://localhost:8080)** into my browser it won't run.I'm logging on the distro as a normal user,would it still prevent root's cron to be run?

---

### Post by cdenley on 2010-02-11
> **Windows95 said:**
> 
I'm logging on the distro as a normal user,would it still prevent root's cron to be run?


No. Verify the script you are running has the correct permissions, and doesn't rely on any environment variables such as "PATH".

---

### Post by Windows95 on 2010-03-02
> **cdenley said:**
> No. Verify the script you are running has the correct permissions, and doesn't rely on any environment variables such as "PATH".

well the first one is I created it under root,the second thing you are talking about...Would you be so kind to explain it to me about it's meaning?I created it under cron.d using nano script while I was logged in as root.Doesn't that make it work on the next startup? :confused:

---

### Post by cdenley on 2010-03-02
> **Windows95 said:**
> well the first one is I created it under root,the second thing you are talking about...Would you be so kind to explain it to me about it's meaning?I created it under cron.d using nano script while I was logged in as root.Doesn't that make it work on the next startup? :confused:

```

#!/bin/sh
touch /test.txt

```
This will not work, I think.

```

#!/bin/sh
/bin/touch /test.txt

```
This will work. Your script will not know where to look for commands unless you specify the full path, or the PATH variable is set. Running a script with cron is not always the same as running a script with a shell. It doesn't have the environment variables.

---

### Post by Windows95 on 2010-03-02
> **cdenley said:**
> ```

#!/bin/sh
touch /test.txt

```
This will not work, I think.

```

#!/bin/sh
/bin/touch /test.txt

```
This will work. Your script will not know where to look for commands unless you specify the full path, or the PATH variable is set. Running a script with cron is not always the same as running a script with a shell. It doesn't have the environment variables.

Thank you but,I believe that wasn't very helpful nor the answer of my question.Could someone please but please explain to me as if you are trying to explain what magna carta is about to your own cat?Thanks again...

---

### Post by cdenley on 2010-03-02
> **Windows95 said:**
> Thank you but,I believe that wasn't very helpful nor the answer of my question.Could someone please but please explain to me as if you are trying to explain what magna carta is about to your own cat?Thanks again...

Well, you can begin by posting your script. You asked about my "second part". A commmon mistake with cron scripts is not specifying the full path for a command. For example, in a terminal, if you want to use the "sudo" command, you simply type "sudo". This then executes the executable file "/usr/bin/sudo". Your shell knows where to look for this binary because an environment variable called "PATH" is set to a series of directories.
```

echo $PATH

```
When cron starts a script, it does not load all the configuration profiles which get loaded when you start a terminal session, therefore does not have a PATH variable set. This means that if you use commands without specifying the full path, the shell will not know where to look for the executable file for that command, and it will fail.

It is difficult to help you with your script if you don't post it.

---

### Post by Windows95 on 2010-03-02
> **cdenley said:**
> Well, you can begin by posting your script. You asked about my "second part". A commmon mistake with cron scripts is not specifying the full path for a command. For example, in a terminal, if you want to use the "sudo" command, you simply type "sudo". This then executes the executable file "/usr/bin/sudo". Your shell knows where to look for this binary because an environment variable called "PATH" is set to a series of directories.
```

echo $PATH

```
When cron starts a script, it does not load all the configuration profiles which get loaded when you start a terminal session, therefore does not have a PATH variable set. This means that if you use commands without specifying the full path, the shell will not know where to look for the executable file for that command, and it will fail.

It is difficult to help you with your script if you don't post it.

Well,I don't mean to blame you but I'm really new to this open source thing and when I don't understand something I get frustrated easily.

Here is my code which I want it to run at every time the pc starts:
```
@reboot /opt/liferay/liferay/tomcat/bin/startup.sh
```

---

### Post by cdenley on 2010-03-02
> **Windows95 said:**
> Well,I don't mean to blame you but I'm really new to this open source thing and when I don't understand something I get frustrated easily.

Here is my code which I want it to run at every time the pc starts:
```
@reboot /opt/liferay/liferay/tomcat/bin/startup.sh
```

That should and probably does execute that script, assuming that script is executable. The script probably fails when run by cron since it relies on the PATH variable as I explained. If you post the script, I can confirm that suspicion. Or, you can try setting the PATH variable:
```

PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin
@reboot /opt/liferay/liferay/tomcat/bin/startup.sh

```

---

