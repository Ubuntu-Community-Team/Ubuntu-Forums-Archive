---
title: "How to SSH to a machine, start a job, and close the SSH session without killing job?"
date: 2011-08-04
forum: Server Platforms
---

### Post by Khufucius on 2011-08-04
Hi guys,

I'm having a problem -- I need to be able to SSH to a machine, run a script (it's a VPN-connection script that needs to run constantly), and then exit the remote machine (closing the SSH session), without shutting down the VPN connection script I started.

How do I close that SSH session without killing the job I've started?  I've tried using "nohup <script> &" but the job dies when I close the console.

I know I must be missing something easy -- how do I keep a job from binding helplessly to the console session that starts it?

Thanks in advance,

_Khufu

---

### Post by Zeosa on 2011-08-04
Easiest thing to do would be to start screen, execute your program in there and detach from the session (ctrl-a d) ..you can re-attach to the session later with 'screen -r'

---

### Post by Gyokuro on 2011-08-04
Hi,

your problem is that you have to redirect somewhere the output and following command should do what you want:  

ssh -n -f user@host "sh -c \"cd /yourdir; nohup ./yourapp > /dev/null 2>&1 &\""

HTH

---

### Post by fdrake on 2011-08-04
ops wrong thread...

---

### Post by dtfinch on 2011-08-04
I've had better luck with setsid than with nohup for some programs.

A second issue is that stdout/err are still attached to your terminal session. When the program tries to print output after the connection is closed, it gets an error, often exiting.

The longer version I sometime use when "setsid program &" isn't enough is:
"setsid program < /dev/null > output.log 2>&1 &"

---

### Post by Khufucius on 2011-08-04
Thanks so much, guys!

-K

---

### Post by msandoy on 2011-08-04
> **Zeosa said:**
> Easiest thing to do would be to start screen, execute your program in there and detach from the session (ctrl-a d) ..you can re-attach to the session later with 'screen -r'

+1 to this.

I have used screen for a year now on my server, and it just works. It's like multitasking for CLI.

---

