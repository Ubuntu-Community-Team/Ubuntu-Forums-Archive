---
title: "Is there a way to see commands ran on the server with a timestamp?"
date: 2010-07-26
forum: Server Platforms
---

### Post by redbrad0 on 2010-07-26
I recently hired a new tech guy to start managing our servers. In doing this I went ahead and upgraded all the servers. It has been awhile now since I sent him the details of the new server and the last time I talked to him he was joking around with one of the other clients not realizing how long it took.

I know on other server moves, my old guy could have everything setup and running in a couple days as a good amount of time is waiting for the data to copy over. I am starting to wonder if this guy is going to try and throw a huge bill at me, so I would like to know what hes doing on the server with time stamps just so I can get a idea of how much time he has been logged into the server. Does this server OS have anything like this built in?

---

### Post by iponeverything on 2010-07-26
The command history is kept in ~/.bash_history though it rolls over, so copy it periodically so data is not tampered with lost. The best way to keep track is run the audit daemon. The "last" command will show you login's and duration.  

You could also put a wrapper around bash which will call "script"command which can save the complete log the session including command output to a unique filename made up of a timestamp and the pid for later review.

Do a "man script" for details. It can replay the session with the correct timing.

---

