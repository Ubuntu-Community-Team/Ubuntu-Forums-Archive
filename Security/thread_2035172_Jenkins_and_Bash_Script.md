---
title: "Jenkins and Bash Script"
date: 2012-07-30
forum: Security
---

### Post by purencool on 2012-07-30
Hi, 

I have set-up Jenkins on my development server and it is great. I am now starting to extend its capabilities.
I have an issue that has to do with permissions. I have created a bash script that when executed will copy the 
Jenkins build into a directory on my web server that displays to the world .

At this point am running in root on my test machine but this not the right way to do things I believe.

Should I make Jenkins apart of the www-data group so that it has the permissions to cp, mv, chmod and chown 
the Jenkins build to the Apache2 root directory path? I am not sure what would be the most secure position 
to take.



Thanks for any help you can give me

---

