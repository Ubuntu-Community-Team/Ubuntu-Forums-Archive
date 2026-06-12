---
title: "webpage on ftp via vsftpd"
date: 2011-08-10
forum: Server Platforms
---

### Post by Senplanet on 2011-08-10
Hello,
I would like to upload webpage on my ftp server and make restricted access with password for known users. I have a lots of directories and subdirectories with files such a images and datafiles which are called from the html code. The webpage works fine if I open it directly from my comp. However if I go via ftp as a remote user, it opens the page , the links to other pages located in subdirectories works fine but the images and files on the webpages are impossible to load.
I use vsftpd ftp server. 
Is this a common problem of ftp or do I need to configure the vsftpd?
Thanks

---

### Post by Wim Sturkenboom on 2011-08-10
I'm missing it a little. To serve webpages, you need a httpd server (like apache), not a ftp server.

So from that perspective, it more than likely has nothing to do with vsftp.

Have you considered case sensitivity for filenames? *Img01.jpg* is not the same as *img01.jpg* in the Linux world. So if this is a Linux server and you've developed under windows, that might be the problem.

---

### Post by Senplanet on 2011-08-10
Let me try to  explain in more details. I need to make a report of my measurements which consist a lots of data . So I have a thousands of graphs and statistics.  I had idea to make a html with links for each plots in subdirectories (each plot on each page) instead of to do a pdf file or something else. I m done with this, it works fine in my comp as  offline page . I have a directory where is the main page and with links to other pages with plots in subdirectories. Then, I got task from my boss to make the page reachable for other colleagues .  So my plan is to just simply copied to our lab ftp as whole directory. I think it should works. The paths of files are universal such a "../data/200906 instead of full path: /home/user/data/200906, so after moving to other comp the paths works fine. Only problem is that the files or images are not visible if I connect to ftp via web browser.
the path for files in the html code looks like > 

<img style="width: 1000px; height: 1000px;" alt="TRHRA" src="file:../analysis/AWS3_1p_2009.jpeg"> 

the paths for other page works fine:

<a href="../main2.html">HOME</a>

So my guess is that the ftp server does not allow the link via "src=" 
but I dont know whether is this common issue or I need to just change something on vsftpd.

---

### Post by Wim Sturkenboom on 2011-08-10
I don't think that it will work as you expect it to work.

How do you connect (view) the pages? Using a browser, I assume; which one? What do you type in the address bar? **http**://something or **ftp**://something

With http, it should not work because the browser will connect to a server that listens on port 80 (an ftp server does not listen on that port). If it works with http, there is a http server runing that serves pages from the specific directory (and subdirectories) and your problem is in the pages that you created.

With ftp you can see the directory contents and you can descend into a directory by clicking on it and you see another listing of files and directories. If you click on a file (e.g. xxx.html), the browser will fetch the file and only has to offer you the option to save it. The browser _**does not have to parse**_ the file (as with http) and therefore it also does not have to fetch images, style sheets etc that you have in there. So if the browser does parse the file, the results might not be what you see with a proper http server,

PS I've never tried to view an html page using the ftp protocol; if it does display the file as a html page, I think that it's only for convenience to get an idea of what the page looks like (which is a lost case if it does not fetch stylesheets, images etc).

PS
```

<img style="width: 1000px; height: 1000px;" alt="TRHRA" src="[COLOR="Red"]file:[/COLOR]../analysis/AWS3_1p_2009.jpeg">

```
I've never used it with *_file:_*; not said that it's wrong; you can try to leave it out.

---

### Post by Senplanet on 2011-08-10
Thanks,
I removed the "file:" from the code, and it really works, but before showing the image it asks me for the username and password again. hmmm interesting....

---

