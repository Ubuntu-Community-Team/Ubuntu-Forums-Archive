---
title: "pCloud app or rclone"
date: 2022-06-19
forum: Ubuntu, Linux and OS Chat
---

### Post by Music_Guy on 2022-06-19
I realize that this question will come down to personal preference in most instances.  Having said that, I'm looking from people's perspective based on their own experiences.  I have a general question.  I'm thinking of using pCloud for cloud  backups.  I can use either rclone or the pCloud app to back up my data.   What are people's opinions as to which would be better?


 As a side note,I have already linked rclone to pcloud (as a free account), and I'm  copying some data to it.  I have also automated the upload with cron.  I do feel fairly comfortable with command line use, so that is not a stumbling block.


 Any and all thoughts welcome.

---

### Post by TheFu on 2022-06-19
I wouldn't upload anything to any cloudy provided that I didn't want shared with the world.  If it was private, I'd encrypt the data BEFORE letting any upload tool even come close to it.  I don't trust the build-in encryption that those tools say they use.  It is fine, but I'd pre-encrypt it.  That goes double for backup data.  

Backup data has sensitive stuff inside it all the time.  Every few months, some security guy finds sensitive keys in cloudy repos or github repos that nobody considered before uploading everything.    [https://nakedsecurity.sophos.com/2019/03/25/thousands-of-coders-are-leaving-their-crown-jewels-exposed-on-github/](https://nakedsecurity.sophos.com/2019/03/25/thousands-of-coders-are-leaving-their-crown-jewels-exposed-on-github/) is scary.

---

### Post by echotech2 on 2022-06-20
See my signature...

---

