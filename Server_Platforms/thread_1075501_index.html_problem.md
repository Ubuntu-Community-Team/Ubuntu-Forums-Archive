---
title: "index.html problem"
date: 2009-02-20
forum: Server Platforms
---

### Post by hooligan36 on 2009-02-20
I have apache 2 running on 8.04. I created a new index.html page on my laptop. I moved it to my server and copied it over to /var/www/ via sudo nautilus. It in turn replaced the pre existing index.html. 

Now instead of the "it works!" message, I am getting a directory view of "index.html".

What do I need to do to get the index view gone and back to displaying a page?

---

### Post by E_K on 2009-02-20
> I am getting a directory view of "index.html".

I don't really understand what you mean here, as you can't have a directory view of index.html as it is a file not a directory,

what exactly does the new index.html file contain?

---

### Post by cariboo on 2009-02-20
When you created the new index.html file did you set the ownership to root and permissions to 755?

Jim

---

