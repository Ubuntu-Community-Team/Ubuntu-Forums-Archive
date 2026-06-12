---
title: "New website/blog"
date: 2008-03-22
forum: The Cafe
---

### Post by totf on 2008-03-22
Hi All,

I recently started a new blog on various topics such such as business, education,  and technology. You can find the site here: [www.simplisticthoughts.com](www.simplisticthoughts.com). 

As I am pretty new at the website thing, can some one please tell me how I could go about hosting a copy of ubuntu or other downloadable stuff on my site. 

Thanks for your help and please let me know what you think of the site.:)

---

### Post by brownknight on 2008-03-22
That is great. Instead of hosting a copy of ubuntu, you could add this script in your website that advertises ubuntu and directs your viewers to [www.ubuntu.com/getubuntu](www.ubuntu.com/getubuntu)

It looks nice too. Here is the script you have to paste to your site.

<script src="http://crunchbang.net/advocacy/ubuntu_199_164.js" type="text/javascript">
</script>
<noscript>
<a href="http://ubuntu.com/getubuntu" title="Get Ubuntu!">
<img alt="Get Ubuntu." src="http://crunchbang.net/advocacy/199_164_ubuntu.png"/></a>
</noscript>

You can see it in action in my site   [http://ramil.blogspot.com](http://ramil.blogspot.com)

P.S. I didnt create this script. It is one Ubuntu gentleman that has it on his website.

---

### Post by totf on 2008-03-22
Thank you. That's a really nice script. The only reason that I was thinking to have it direct from my site (if that's okay) is that I want to make it really simple for anyone who wants to try ubuntu. Directing them to another page adds one more step. Let me know what you think. By the way i really like your blog

---

### Post by brownknight on 2008-03-22
Thank you. If you dont mind I have some comments why it is better to have it hosted on ubuntu website...

1. People downloading it may have different system needs (x86, 64bit, PPC)
2. They might want the server or the desktop edition
3. They might be from a different location (US, Asia, Europe)

So you would need to have all these options available on your website and lastly, I think it is better to have it from the official site. These are my personal opinions.

---

### Post by totf on 2008-03-22
Yeah, those are some good points. I think you are probably right to have it posted on the main site. Just in the past, when I tried to have some one dl it they were confused with all the options. I think I will just send a link to the main site like suggested. 

In the meantime, can someone tell me how to host files on my own site, in case I have the need in the future.

Thanks

---

### Post by ad_267 on 2008-03-23
You need to use ftp access to upload a file to your website. Open up nautilus and in the location bar enter the ftp address of your website host (e.g. [ftp://ftp.yourhost.com](ftp://ftp.yourhost.com)) and then enter your ftp username and password and from there you can put your files somewhere in the htdocs folder (it may be called something else, but this is the directory that index.html or index.php is in) and maybe make a new subdirectory for your files and then just link to them from your website.

Edit:
When creating a link to a file the root directory is the htdocs directory, so the link will be to http://simplisticthoughts.com/yourfilesubdirectory/file.extension, where "yourfilesubdirectory" is a subdirectory of the htdocs directory.

If you didn't upload your wordpress files yourself then you might not know your ftp details. Your web host will be able to tell you these.

---

### Post by totf on 2008-03-23
Thank you very much for your help. I didn't install wordpress myself, but I think I will be able to find the folder.

Thanks again

---

