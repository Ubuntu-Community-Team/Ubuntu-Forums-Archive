---
title: "Reddit Code with Python, Postgres and Cassandra"
date: 2013-06-29
forum: Server Platforms
---

### Post by Snitz on 2013-06-29
I'm trying to install Reddit Code ([https://github.com/reddit/reddit]("https://github.com/reddit/reddit")) on Ubuntu 12.04.

I already installed it locally on my laptop and it worked, the process was smooth.

But now that I'm trying it on a live node, I keep getting errors regarding Cassandra. It says that Cassandra cannot connect to localhost port 9160. I didn't have that problem when I worked with locally.

Reddit Code requires a list of dependencies for it to work: [https://github.com/reddit/reddit/wiki/Dependencies]("https://github.com/reddit/reddit/wiki/Dependencies")
They even have an automated installation script for Ubuntu 12.04: [https://github.com/reddit/reddit/wiki/reddit-install-script-for-Ubuntu]("https://github.com/reddit/reddit/wiki/reddit-install-script-for-Ubuntu")

But I guess you need to install the dependencies manually first before you run that script.

Any help and advice is appreciated. Thank you for your time.

---

### Post by DJ_Max on 2013-06-29
Did you check to see if anything was running on that port? What processes may be started already. Did you follow directions in the README.txt?

---

### Post by Snitz on 2013-06-30
I did a netstat and it turns now cassandra wasn't even running. Turns our it was crashing on 512mb ram machine. So I upgraded to 1GB and it worked smoothly.

---

### Post by DJ_Max on 2013-07-02
Good deal, sometimes error messages can mean more than the obvious message it's portraying.

---

