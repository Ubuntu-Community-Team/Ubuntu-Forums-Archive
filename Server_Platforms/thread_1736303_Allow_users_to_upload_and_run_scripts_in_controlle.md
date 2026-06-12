---
title: "Allow users to upload and run scripts in controlled environment?"
date: 2011-04-22
forum: Server Platforms
---

### Post by mrwooster on 2011-04-22
I am setting up a small competition for a forum where there are a set of programming tasks to complete (in various languages).  At the end of the allocated time, the fastest program that successfully completes the task wins.

I would like to set up a server similar to the way the Google AI challenge works, where users can upload code to the server via an html page and the code is executed and profiled on the server.

The problem is obviously security... so... how can I configure my server so that the uploaded scripts are run in a completely jailed environment and do not have access to anything outside their folder and cannot execute any commands on the server?

The chain of events looks like this: User writes script on local machine -> user zips script -> user browses to server html page -> user uploads script -> script is compiled and executed on the server -> user is shown output from script.

Ty

---

### Post by elico on 2011-04-22
it depends on the programing language.
there are platforms to jail scripts on servers for python.
it's not really recommended to let anyone run scripts on your server.
if it's specific tasks you can make simple code check and make sure that specific libs will disqualify the code from running.

i think you want to consider this matter with a "compiling farm" operator\sysadmin.
look at
[http://gcc.gnu.org/wiki/CompileFarm](http://gcc.gnu.org/wiki/CompileFarm)

---

