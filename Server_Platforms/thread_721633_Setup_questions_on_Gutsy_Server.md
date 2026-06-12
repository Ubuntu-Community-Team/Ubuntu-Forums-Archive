---
title: "Setup questions on Gutsy Server"
date: 2008-03-11
forum: Server Platforms
---

### Post by AaronMiller on 2008-03-11
So I've setup a small business with a small Gutsy server to do very basic things for them. The only thing it really does is provide a file server for them to place files that they need to share between multiple computers so there aren't 50 revisions of the same file floating around.

All employee's have an account on the server which houses their personal documents that other users cannot see, then there is a shared directory that all users can see and edit to, and a finance directory that only certain people can view. That's all functioning and working for them for the most part. Here is what isn't setup so far and I'll need some help or pointed in the right direction on how to set them up.

The business wants to have backups take place every so often (they are not sure entirely on how often yet). For starters I am going to set them up with a weekly backup so it takes all the information out of the /home directories and puts them into a nice compressed tar and then placed on the hard-drive. Then every month they'd like to have the files burned to a DVD for archiving purposes. I'm not sure that all their data is going to be able to be stored on one DVD so I suggested they invest in an external hard-drive to take to and from every day. What I'd like to setup is the following:

[LIST=1]
[*]An e-mail gets shot out to the owner of the business reminding them that he needs to put in a DVD or plug in the external hard-drive tonight.
[*]The server then over-night backups all of the files onto the hard-drive preferably zipped so that it's easier to see from a Windows XP machine.
[*]Then the server will send an e-mail back to the owner saying if the backup was successful or not.[/LIST]Also, I need to setup a way for the owner to access the files on server from home, then save the back to the server from his home to work on them some more when he gets back into the office. I was thinking VPN? Is that the right area or am I off?

Lastly, I bought a hardware external modem for him to use on his server. Basically he gets a lot of spam faxes for advertisements that he doesn't want to spend money and ink on to print out. I loaded up Hylafax onto the server and I *think* its working (its not hooked up yet or tested with answering faxes). What we need to get setup is the ability to have the faxes come in be answered by the server then send a PDF/E-mail to the owner with the fax so he can view it before printing it out. 

Any help with this would be greatly appreciated!

---

### Post by afbase on 2008-03-11
> 
1.  An e-mail gets shot out to the owner of the business reminding them that he needs to put in a DVD or plug in the external hard-drive tonight.

Make a cronjob (crontab) that telnets to an smtp server to send out a message.  It may take a several lines to write in a bash script.



> The server then over-night backups all of the files onto the hard-drive preferably zipped so that it's easier to see from a Windows XP machine.

Not really sure how extensive this back up is but it sounds some kind of a hefty backup.  Start [here](http://jeremy.zawodny.com/blog/archives/010037.html).

uhhhh the step 3 could be done by a another script ran by a cronjob as well.

---

### Post by AaronMiller on 2008-03-11
Thanks, any ideas on the VPN or fax issues?

---

### Post by AaronMiller on 2008-03-12
Bump!

---

### Post by hyper_ch on 2008-03-12
it would be much simpler to make backups to another computer... not much cpu needed here... a slug2 with some nice harddisk would do fine... preferreblay at another location....

I do every 6h a backup onto my 750gb drive and during the night I make an incremental backup trough SSH to my other computer at my parents' house.

---

