---
title: "Bandwidth Speed Question"
date: 2011-01-24
forum: Server Platforms
---

### Post by garfonzo on 2011-01-24
Hey Folks:

If I have a server with a bunch of company data files, and the employees who access the data are in an office in another state/province, how much bandwidth could I burn through each month, and what upload speeds would you say is necessary?

Let's say that there are 3-4 employees accessing data all day, 8-5 and that the only files are MS Word, Excel, and Access. 

Any thoughts?

---

### Post by wongo888 on 2011-01-24
I set up a system like that once about 8 years ago. We did it with a single T1 connection and it was fine. You won't know the real answer until you build it though.

---

### Post by volkswagner on 2011-01-24
Sorry, but I must ask.

Are all the employees in the same location/office?

If so, why not locate the server at the office, and administer it remotely?

Bandwidth and speed are difficult to estimate with no past history or knowledge of file size and number of users.

You will need good upload speeds at your location, matched with good download speeds at the office location.

---

### Post by garfonzo on 2011-01-24
> **volkswagner said:**
> Sorry, but I must ask.

Are all the employees in the same location/office?

If so, why not locate the server at the office, and administer it remotely?

Bandwidth and speed are difficult to estimate with no past history or knowledge of file size and number of users.

You will need good upload speeds at your location, matched with good download speeds at the office location.

That's a good question. The argument against not having the file server at the office is twofold:

1) I live 1,100 miles away from the office so if anything ever goes wrong with the server itself (hardware or otherwise), there is no way I can get to it in any reasonable time and the employees would have no idea how to help
2) The employees spend a lot of out-of-office work time, which means accessing the files across the internet is essential. Further, there are MS Access databases which are often opened by more than one user at a time so an FTP solution is not possible.

The combination of both of the above makes me think, I might as well physically plant the server at my location and serve files from here. 

It seems that the best upload speed I can get at my location is 1Mb/s as a residential business user. I would have to have a commercial space to set up anything faster (T1, fiber). I am doubtful that my boss would rent an office space just to house the server (but who knows I suppose). 

I don't want to "find out when I build it" because I don't know if this is the best way to serve the files. I am trying to gather as much information on a number of solutions to serving files before I present a solution to my boss.

---

### Post by wongo888 on 2011-01-24
Go check out the logs in the current server. That would give you an idea about current usage.

You might want to look at Amazon EC2 if you are thinking about a colo. Ubuntu runs well on EC2.

---

### Post by garfonzo on 2011-01-24
> **wongo888 said:**
> Go check out the logs in the current server. That would give you an idea about current usage.

You might want to look at Amazon EC2 if you are thinking about a colo. Ubuntu runs well on EC2.

That's a good idea about checking the current server's logs.

---

### Post by nevyndweomer on 2011-01-25
how about this for an idea 

have a local server for the users which will save you on bandwidth and then do an over-night syncronise to a backup server at your location.  

If the primary ever goes bang then you can serve the users from the backup server until you can arrange repair/replacement. 

1) Users get a better response time under normal operation 
2) you have a redundant solution in case of failure 
3) The users will accept a degraded service in a failure scenario so you will not have to spend oodles of money on bandwidth.

---

### Post by garfonzo on 2011-01-25
> **nevyndweomer said:**
> how about this for an idea 

have a local server for the users which will save you on bandwidth and then do an over-night syncronise to a backup server at your location.  

If the primary ever goes bang then you can serve the users from the backup server until you can arrange repair/replacement. 

1) Users get a better response time under normal operation 
2) you have a redundant solution in case of failure 
3) The users will accept a degraded service in a failure scenario so you will not have to spend oodles of money on bandwidth.

That is a very interesting solution. The added bonus is that I can completely configure the local server first (setting up remote SSH abilities) and then ship it off to head office and have them plug it in and boot it up. Once online, I can complete all the configuration remotely. Then, have the second server at my place continuously syncing itself to the server at HQ. 

Cool idea. 

I do have an additional problem, though, which I didn't want to focus on here. I have a thread going [over here]("http://ubuntuforums.org/showthread.php?t=1674677") where I discuss the employees' needs to have continual access to their files beyond the LAN environment. This makes things a little trickier. To complicate things more, they have MS Access files (databases) which can, and must be, opened by multiple users at the same time for editing. It is a complicated situation that I am trying to figure out how to handle. I thought I would start with the bandwidth question and move from there.

---

