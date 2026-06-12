---
title: "File upload does not work using apche and php"
date: 2010-07-17
forum: Server Platforms
---

### Post by ManavGoel on 2010-07-17
Hey people, 
  I am a new member of ubuntu forums. I am currently using apache2.2 and php5 on ubuntu lts 10.04. 
The problem I am facing is that file upload not working using php
.Everything works fine,there are no errors in uploading except when move_uploaded_file does not work. When problem first came up,I found that you have to set user permissions to allow apache to write files.So I changed permission of /home/manav/www (which is my default directory for localhost) to 777.
From then sometimes upload works and sometime does not . I am really confused now what to do. If I have not posted in right category ,kindly tell where to post . :)

---

### Post by timothy_tim on 2010-07-17
It isn't recommended to the 0777 permission to a file.  It's preferable to use 0644.

De default user for the web server is www-data. You could check if every folder or file is writable to this user.

---

### Post by Sanjeevtrip on 2010-07-18
as timothy_tim pointed out correctly 0777 is not recommended.
in your case you /home is restricted others go write
create /var/www which has 0644 also your /var should have 0755 to work.

---

