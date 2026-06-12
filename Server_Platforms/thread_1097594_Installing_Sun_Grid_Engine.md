---
title: "Installing Sun Grid Engine"
date: 2009-03-16
forum: Server Platforms
---

### Post by muxecoid on 2009-03-16
Hello. Maybe Ubuntu is not the best distro to install SGE but I'm already familiar with it. I see gridengine on the repository but I can not configure it properly. Is there a guide to configuring it? If no do you know any newbie-friendly guides to installing it from Sun official binary (other that doc at Sun website which is excessively technical)?

---

### Post by mert on 2009-06-29
I also need to get SGE running on ubuntu.  I just discovered that there is some documentation and a quick start guide in /usr/share/gridengine-common (of all places!) .  I will try to get it running and let you know how it goes...

---

### Post by NaitoNeko on 2009-08-13
Any news about this post ? I also want to know about the configuration of SGE in ubuntu.

---

### Post by hwttdz on 2009-08-23
I successfully installed pbs, but now I'm thinking of switching to sge.  It does seem to have a few advantages.

---

### Post by hwttdz on 2009-12-11
Sorry to wake a long gone thread, but I set up sge successfully (on a few different machines).  So if you have any questions let me know and I'll see if I can help any.  The big ones I came up with are just making sure you add your machine as both an execution host and a submit host, and making sure the name matches that from your hosts file exactly. 

A quick detail of my install, I'm sure missing the useful bits: [http://astoryworthtelling.wordpress.com/2009/08/25/installing-sge-on-ubuntu-single-machine-local-install/](http://astoryworthtelling.wordpress.com/2009/08/25/installing-sge-on-ubuntu-single-machine-local-install/)

---

### Post by HighCommander540 on 2009-12-13
Not to be a dick about this or anything, but why wouldn't you just use Ubuntu's built-in cloud clutering technology?

---

### Post by hwttdz on 2009-12-13
I use sge because it's easy to use and does what I want, there are also other reasons.  For instance to submit the job "echo 'hello world'" to sge the command is 

qsub -shell n -b y "echo 'hello world'"  (some might prefer qrsh)

what would the command be using ubuntu's cloud system? 

Other reasons:
1) because the documentation is better
2) because it (or similar queuing systems) are standard in compute environments
3) because I am familiar with the environment and I can make scripts which run on both my local instance of sge and other queues on which I work
4) sge is designed to manage computationally intensive jobs, whereas the ubuntu cloud management is not (the overhead of running a vm seems silly)

---

### Post by jefftb82 on 2009-12-16
hwttdz, 

do you have any more information on installing sge?

J

---

### Post by hwttdz on 2009-12-16
Well for a single machine install (which granted is an unusual situation, but for a quad core processor I feel allows me to use the processor quite a bit more effectively).  First install everything you're going to need:

sudo apt-get install gridengine-client gridengine-common gridengine-exec gridengine-master gridengine-qmon

I think it also installs a few other things, like lesstif2 and bsd-mailx, choose automatically configure, then for the cell name I just named it sge_cell or somesuch, doesn't seem to come up.  The admin host is the hostname of your head machine, i.e. $HOSTNAME and then you get back to the command prompt. 

Run "sudo qmon" to get a nice graphical interface to administer your mini-cluster.  The first thing to do is add a queue, so go to queue control, then add, you're going to want to change the name, I just went with $HOSTNAME_queue, I changed slots to be the same as the number of processors, and I changed the shell to be the bash shell.  Exit queue control.

Go into host configuration and add $HOSTNAME as a submit host (it should already be listed as both an admin host and an execute host).  Back to main menu.

I went into the scheduler and changed the scheduler time to something shorter than 15 seconds, I often submit a large number of jobs none of which take terribly long, and I don't think that the sge scheduler uses up much in the way of cpu cycles, so I moved mine all the way down to 3 seconds from the default of 15. 

Finally you should be good to go.  Try, 

qsub -j y -o /dev/null -N test_job -q $HOSTNAME_queue -cwd -V -b y "echo 'hello world' > my_output.txt"

Where
j = join output and error
o = send output to 
N = name
q = queue name
cwd = do in the current working directory (no effect in this case)
V = save environment variables, in this case the path, otherwise "echo command not found"
b = binary?
finally a command

Let me know if you have any more issues.

I assume if you wanted to put more machines in the mix as exec hosts, you would need to install at least gridengine-exec on them (possibly common and client as well), and then add them as exec hosts, adjusting the number of slots in the queue as necessary.

---

### Post by jefftb82 on 2009-12-17
Hey hwttdz, 

Thanks for the response and the extra info.  I have done everything you have listed.  Iam currently testing on a single machine for master and compute node but will be extended in the near future(if I can ever get it going).  

My main problem is that I keep getting this error whenever I submit a job.  

"your job is not allowed to run in any queue"

Any idea's?

J

---

### Post by hwttdz on 2009-12-17
What's the output if you do "qstat -g c" (as the user from which you are going to be submitting jobs), then "qstat -g c -U username", the first asks the queue manager what the status of all the queues is the second asks the status of the queues to which that user can submit.  If the second is empty then you probably need to add your user as a user who can submit to the queue.  This is weird, because I did a purge on all my gridengine before following the instructions I posted, which means I didn't make any config changes like that, so the default allows any user to submit to the queue.

---

### Post by hwttdz on 2009-12-17
And if you submit with -q queue_name do you get the same error? (I think the default behavior if you don't specify a queue is that it sends the job to the default queue).

---

### Post by jefftb82 on 2009-12-17
> **hwttdz said:**
> What's the output if you do "qstat -g c" (as the user from which you are going to be submitting jobs), then "qstat -g c -U username", the first asks the queue manager what the status of all the queues is the second asks the status of the queues to which that user can submit.  If the second is empty then you probably need to add your user as a user who can submit to the queue.  This is weird, because I did a purge on all my gridengine before following the instructions I posted, which means I didn't make any config changes like that, so the default allows any user to submit to the queue.

I get...

CLUSTER QUEUE                   CQLOAD   USED    RES  AVAIL  TOTAL aoACDS  cdsuE  
--------------------------------------------------------------------------------
jeffq                             0.19      0      0      2      2      0      0

and i get 

CLUSTER QUEUE                   CQLOAD   USED    RES  AVAIL  TOTAL aoACDS  cdsuE  
--------------------------------------------------------------------------------
jeffq                             0.36      0      0      2      2      0      0 
error: no queues remaining after -U queue selection

if i do a -U username

J

---

### Post by hwttdz on 2009-12-17
Ok, I know this is a very windows like solution, but try rebooting as that will restart all the sge services, and it's possible that it needs to refresh the users list, and I don't know how to do that without restarting the service.

---

### Post by jefftb82 on 2009-12-17
will give it a shot soon.  Thanks!

J

---

### Post by hwttdz on 2009-12-17
Oh, this is more likely the problem, that your hosts file isn't configured correctly, if you look in qmon to find the submit host, i.e. hostname, 
if you type "ping hostname -c 1" does it work out?  If not you might have to edit your hosts file.  The significant lines of mine read:

192.168.###.###	hostname
127.0.1.1	fully.qualified.hostname	hostname

Where 192.168.###.### is my ip on my local net, in fact you may want to make sure your hosts file is set up proper anyways (I'm sure there are still errors in mine, this is one thing I wish was properly setup automatically).

---

### Post by jefftb82 on 2009-12-17
I tried that.  My hosts config seems to be correct.

---

### Post by ashkan720 on 2010-08-10
hello all
it's really urgent situation!
this is my first post in this forum
I'm try to install and run sun sge in ubuntu 10.4 and use it beside FSL ([http://www.fmrib.ox.ac.uk/fsl/](http://www.fmrib.ox.ac.uk/fsl/)) 

I installed grid engine from great ubuntu repository.

first where is settings.sh ?
In sge classic (!) install way it's very important to load settings.

and MOST IMPORTANT!!!!
sge is working very good, it does sample jobs and every things is okay. 
but when i'm trying to submit jobs from FSL the job state become Eqw and error message is 
***can't chdir to <my_job_path>: No such file or direct***

why?
chdir is a csh command, I installed csh. what can I do next?!
Please help me
thank you all

---

### Post by moxgreen on 2010-08-13
> **hwttdz said:**
> I use sge because it's easy to use and does what I want, there are also other reasons.  For instance to submit the job "echo 'hello world'" to sge the command is 

qsub -shell n -b y "echo 'hello world'"  (some might prefer qrsh)

what would the command be using ubuntu's cloud system? 


It would be very useful for me if someone can answer this question.
I'm evaluating SGE vs Eucaliptus.

---

### Post by alexsavio on 2011-07-28
Hi,

I'm having the same problem.
When editing fsl_sub, what should I put in fslcluster_cell_settings??
I tried /etc/gridengine/configuration and when I ran a bedpostx test, hundreds of xterm windows appeared on my screen although the job ran and worked. Weird!

Using Maverick amd64 here.

Any suggestion?

Thanks!

---

### Post by alexsavio on 2011-07-28
Found the answer:

[https://www.jiscmail.ac.uk/cgi-bin/webadmin?A2=ind1102&L=FSL&P=R10155&1=FSL&9=A&J=on&d=No+Match%3BMatch%3BMatches&z=4]("https://www.jiscmail.ac.uk/cgi-bin/webadmin?A2=ind1102&L=FSL&P=R10155&1=FSL&9=A&J=on&d=No+Match%3BMatch%3BMatches&z=4")

---

