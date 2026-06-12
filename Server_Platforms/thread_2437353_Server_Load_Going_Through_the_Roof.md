---
title: "Server Load Going Through the Roof"
date: 2020-02-22
forum: Server Platforms
---

### Post by markshepparduk on 2020-02-22
Hello Everyone,
I have woken up this morning to find my server resources going through the roof. I know the server updated yesterday and now all the resources seem to be maxed? How can i see what is hogging the resources to find out what the issue is please? I am using Ubuntu Server 18.04 with Virtualmin.

Thanks

Mark

---

### Post by TheFu on 2020-02-22
I would assume you've been hacked and the server is running crypto-mining software.

Step 1 - unplug from the internet.
Step 2 - use system tools to see which processes are using the CPU, RAM, network and storage.  top, free, vmstat, netstat, du, lsof are my initial go-to tools.
Step 3 - now that you figured out the program, you can check your versioned backups to see which files changed when you didn't change them. New files that showed up on the system around the same time should be suspect too.  You can also compare the old and new files to see WHAT the changes were for text/scripts.
Step 4 - figure out how they got in and close that vector.  My first hunch would be any webapp that was mis-configured, especially any written in php.  2nd hunch would be crappy login credentials.  Only ssh using key-based authentication should be possible to log into the server.  Those web-based admin tools? Those should never be available except from the "localhost" interface, so an ssh tunnel is required to access them.

Stay patched.  Weekly is what we do, but sometimes, if there is a directed attack against specific tools that we use, we'll patch those ASAP.  This happens about once every 3 years, but much of our good luck is due to some policies we have against using commonly hacked solutions.

If you can't 100% prove that the system hacks are known and solved, then it is time to wipe the box and start over fresh. Perhaps rethink the network architecture from a securty-first standpoint?

Hopefully, you have an alarming and monitoring setup to catch issues like this. Perhaps it is working and notified you.  If not, once you get everything rebuilt.

Or, if this isn't a pure server, perhaps a bad GPU driver is to blame?  The process using all the CPU will say much.

And checking the system log files for errors and warnings is always smart.

---

### Post by EuclideanCoffee on 2020-02-22
When my server uses too much resources, it's likely related to an application mismanaging memory. We see this a lot in the server realm.

To troubleshoot, you begin with finding the root of the problem. I use ps, pstree, and top.

I use top to see if there are any processes I recognize running. If not, I use a combination of `ps aux` and `ps ea` to find the process number running at a high memory.

One problem that is common is a daemon that simply repeats itself enough times that it creates thousands of processes that do one simple thing, but that is one simple things thousands of times. To kill this process chain, simply pkill -9 # of the parent process, and it will resolve itself typically.

This thread provides some sleek bash hacks to make the ps stdout readable, but I simply use the four commands above whenever troubleshooting a run on computer. [https://unix.stackexchange.com/questions/13968/show-top-five-cpu-consuming-processes-with-ps](https://unix.stackexchange.com/questions/13968/show-top-five-cpu-consuming-processes-with-ps)

---

