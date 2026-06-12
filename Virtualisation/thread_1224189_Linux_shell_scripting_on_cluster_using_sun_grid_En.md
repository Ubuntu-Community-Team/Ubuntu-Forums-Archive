---
title: "Linux shell scripting on cluster using sun grid Engine"
date: 2009-07-27
forum: Virtualisation
---

### Post by Kabelom on 2009-07-27
Good day ..i am a student and i am been trying to experiment by writing a shell scripting using SGE commands & awk &sed commands without any success .the script has to output system statistics eg the types of queues (Jobs Available,Jobs Waiting ,Jobs Errors) and the quota ..it has to display when the user log on the cluster .it has to be a summary ..the main aim the user doesnt have to use qstat command when he is on the cluster ,the script has to simplify the users work

even if the script doesnt use other commands as long i can try to get ideas or script that can give me the output i want ..please help

---

### Post by Claus7 on 2009-07-27
Hello and good day to you!

I think that what you want to do is to create a script which will run during logging in and will display necessary information to every user. In order to do so you can write one and place it in /etc/profile 

The thing is: why the user should not use qstat while he or she is logged in? For example, I am a user and I connect to the cluster. Then I stay there and work for about an hour. If I want to see the stats I have to log in again? These are important info for a cluster usage that a user should be able to access at any time. Things are changing all the time. Anyway. 

In order to create the script you want, you just have to include to it the commands you think are necessary (their output is necessary for the user) and then make this script exetutable. Place it somewhere and then inform /etc/profile about its existence.

Regards!

---

