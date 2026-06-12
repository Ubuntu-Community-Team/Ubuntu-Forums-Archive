---
title: "How to securely give permissions to my user and www-data?"
date: 2022-11-18
forum: Security
---

### Post by forumate on 2022-11-18
I created a Laravel project using my user. But now I added code that creates folders and files. The files and folders created by the PHP code are owned by www-data user and group. So when I check ownerships and permissions inside the root directory, I see the entire project is a mix of different ownerships for the folders and files, of my user and www-data.


That happened because the project itself was created by me so most of the files are owned by my user name and user group. 


But now as I work on the project, I'm writing code that makes the web server create files and folders and it's owned by www-data user and group.


The problem is I am using VSCode Remote (with SSH) and then I can't access/edit the files created by the server with my user so I just chown every time, because I'm currently working on a file storing script. So I want to see if my script worked and created the correct files so I have to chown it right now to access them


But how can I make my user be able to also view/edit the files created by www-data securely without needing to chown every time?


I know there are a few approaches and I was recommended by some to use setfacl command. Or maybe I should add my user to www-data group? But I was told me this approach is bad (in production) because if someone gets access to the web server he gets access to the entire system.


What would be a good practice to allow my user to access (read/write) files created by the server.


Also, since the rest of the project is owned by me (not newly created files), should I also changed that to be owned by www-data?

Can you please help me with the commands as well? This is something I haven't done before

Thanks

---

### Post by TheFu on 2022-11-18
So, there are many opinions on this specific topic.

Generally, it is a bad idea to modify files directly that are being used in any webapp.  You want a common, repeatable, process, to deploy new code, ensuring that it comes from the DVCS, gets processed to remove sensitive files, converts images to 'web optimized' versions and sets all the specific owners, groups, and permissions EXACTLY as needed.  In general, you don't want any end-user's account to have write access to these web-app directories.  That is just more risk.  Users are seldom good at security. Heck, even security professionals make 1 mistake every few weeks, so what chance to normal users have?

Also, you don't want www-data (user or group) to have write access exact to a specific "upload" directory that cannot be seen by any web-app users.  Uploads need to be 1 way, not available to anyone, until some processing of those files are performed to ensure they aren't conveying malware or any other unwanted, hidden, code.

So, a deployment script should be pulling the code from the repos, running all the optimizations, run chown/chgrp/chmod across the entire project to get exactly the required permissions, where they are needed.  All of this can be automated using a bash script with those commands.

---

