---
title: "cant upload large files to webserver"
date: 2009-07-26
forum: Server Platforms
---

### Post by kennedy7 on 2009-07-26
Hello guys. I host 5 websites, 3 private and 2 public, and i use a php  filemanager and have video sharing pages that people upload things to. I have set everything in php.ini to the correct settings. upload_max 5120M,
post_max 5120M and everything else that involves upload. But so far it wont attempt to even upload the file to the server. The harddrive i try to upload it from is working away but its like the server isnt even receiving the file. I have posted php.ini as an attachment. What i would like to be able to do is to be able to upload the biggest size file possible without it timing out. Thanks in advance. I had to change the file extension to be able to attach php.ini so just change it back to php.ini when you look at it

---

### Post by HermanAB on 2009-07-26
Does the file system support files larger than 1GB?

---

### Post by kennedy7 on 2009-07-26
I am using Ubuntu 9.04 server with 80gigs of harddrive and ext3 filesystem and yeah it does support files larger than that. It just wont upload files bigger than 1gig

---

### Post by hessiess on 2009-07-27
Check that your PHP file manager isn't programmed to block files larger than a gig, for example if the 

```

<input type="hidden" name="MAX_FILE_SIZE" value="some_value" />

```

feild in the HTML form is set to small, the browser will drop the file without even attempting to upload it.

---

### Post by grantemsley on 2009-07-27
I don't know what's causing your problem...however, I would strongly recommend using FTP or some other means of transferring files that large.

---

### Post by kennedy7 on 2009-07-27
Well, it isnt just in my filemanager it is on every upload script i have ever used, so i dont know what is wrong

---

### Post by Hobgoblin on 2009-07-27
It sounds like it's hitting the php script execution timelimit.

Try increasing max_execution_time in php.ini

---

### Post by kennedy7 on 2009-07-27
What should i increase it to to be able to upload 5gig files?

---

### Post by kennedy7 on 2009-07-27
its not even attempting to upload files over 1gig. Its not in the php script though. maybe something in php.ini

---

### Post by grantemsley on 2009-07-27
It's not even trying to upload it, or it timed out?

Have you tried with different browsers?  If it's not even starting the upload, it might be a browser issue.

---

### Post by kennedy7 on 2009-07-27
i have tried all the browsers i can think of. and its not even starting the upload. I have a video sharing script called ostube and it also lets me set a upload limit but i have that set to 5120M which is 5gigs. so It isnt even starting the upload. The browser says "sending request..." and than after a while it just quits but when i am uploading i see nothing in the /tmp folder as when im uploading a smaller file.

---

### Post by weather15 on 2009-07-28
The problem it that all major browsers do not allow you to upload files larger than 2GB.

---

### Post by kennedy7 on 2009-07-29
But i cannot even upload 1gig files with firefox

---

### Post by kennedy7 on 2009-07-31
I can upload 8gig files with webmin with firefox to my server

---

### Post by HermanAB on 2009-07-31
Divide and conquer...

Install a regular FTP server and confirm what is going on.

---

### Post by kennedy7 on 2009-07-31
Ok, well ill start using webmin filemanager, even though java takes a while to load

---

