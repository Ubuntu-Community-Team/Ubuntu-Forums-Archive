---
title: "EC2 newbie questions"
date: 2011-03-29
forum: Ubuntu Cloud and Juju
---

### Post by mathuin on 2011-03-29
I'm mostly satisfied with my EC2 experiences to date.  However, I'm interested in learning some more about current best practices.

Ideally I'd like to start the machine up, run a job, have it push the results somewhere, then terminate itself.  What's the best way to do this?  I'm using ami-cef405a7 as my AMI, which has no EC2-specific features to the best of my knowledge.  I wrote a short script to install about a hundred packages and build  some stuff from source to turn a stock Maverick 64bit instance into what  I need for my project -- takes about eight minutes to run on a micro  instance.  Can the user data or key-value pairs be reached easily from the shell?  That'd be enough for me to run a job.

The other major question: how to move data *off* the instance before shutting it down.  Since the instance would run unattended I think my options are limited to copying an ssh private key up to the instance and using that for rsync/scp/what-have-you.  Are there other alternatives I haven't seen?

Thanks for all your help.  I'm really enjoying EC2 and I just want to make the most of it.

Jack.

---

### Post by kim0 on 2011-03-29
Hi Mathuin,

Let me try to help :)

- Just a note about the ami-id .. you can always find the latest by checking out [http://cloud.ubuntu.com/ami/](http://cloud.ubuntu.com/ami/)

- The official AMI you're using, has ec2 specific features, like cloud-init: [https://help.ubuntu.com/community/CloudInit](https://help.ubuntu.com/community/CloudInit)
Cloud-init allows you to do various things to customize a generic image as it boots. It's mostly a cleaner form of running a user-data script .. but since you've already written that, maybe just stick to it! You can learn more about cloud-init from my blog posts [http://foss-boss.blogspot.com/search/label/cloud-init](http://foss-boss.blogspot.com/search/label/cloud-init)

- About reading from user-data .. How are you running your script today ? I suppose you're passing it as a user-data file, if so, why aren't you embedding the values you want inside the script .. Any way, yes a shell script can read values from the user-data service at the following URL [http://169.254.169.254/latest/user-data](http://169.254.169.254/latest/user-data)
Example: curl [http://169.254.169.254/latest/meta-data/public-ipv4](http://169.254.169.254/latest/meta-data/public-ipv4)

- For getting data off the instance .. yeah .. what you describe would work .. However, I feel it would be cleaner to have a ec2 "volume" that always has your data on it. So the workflow basically would be
1- You start your instance
2- Attach volume to instance .. mount it
3- Instance crunches on data (from volume, or downloads more data) ...etc
4- You terminate instance .. the volume remains .. waiting till next instance (of course you pay for the volume storage)

For an example of that, check out this article of using an external volume to hold mysql data on it .. it's similar to what I just described. [http://aws.amazon.com/articles/1663?_encoding=UTF8&jiveRedirect=1](http://aws.amazon.com/articles/1663?_encoding=UTF8&jiveRedirect=1)


Can you let me know what you're doing .. I'm interested in what data is being crunched :)

---

### Post by mathuin on 2011-03-29
I have a project [http://www.mathuin.org/TopoMC/](http://www.mathuin.org/TopoMC/) and I'm using EC2 to generate content so my home computer isn't completely useless for a day or so at a stretch. :-)

The script I have written does the following:

[LIST]
[*] fusses with sysctl fs.file-max if necessary
[*] changes nofile values in /etc/security/limits.conf if necessary
[*] populates .ssh/known_hosts with my home system and my hosting provider
[*] populates .ssh/config with necessary config info for those systems
[*] populates the ssh key I generated for EC2 use for both (insecure probably, sigh)
[*] retrieves the scripts I use to generate the content
[*] runs apt-get update and then installs over 100 packages (sigh!)
[*] checks out several git repositories
[*] builds the code in one of the repositories
[*] downloads, builds, and installs python-suds (which is *not* available as a package AFAIK)
[/LIST]
Once this is done, the instance is ready to go -- I just log in, start up screen, use term 0 for top and term 1 for my app and I'm off to the races.

I need to modify my script to run as root instead of ubuntu and then I can try it out in user-data land.  The curl trick looks interesting, but I can't see how to access the key-value pairs with either that or cloud-init.  It is a goal of mine to automate the entire process from startup to shutdown -- any idea how to get to those key-value pairs?

As for saving state, at least right now the project is in sufficient flux that I need to regenerate my data every time so maintaining an EBS volume wouldn't help.  I will definitely keep it in mind for the future, though.

Jack.

---

