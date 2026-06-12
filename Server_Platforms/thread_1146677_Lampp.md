---
title: "Lampp"
date: 2009-05-02
forum: Server Platforms
---

### Post by kurtisnathan on 2009-05-02
I downloaded, extracted, turned on, and tested XAMPP for Linux, but I can't save any files into this folder, so apart from the index.php, I cannot open or save any .php files. I open the properties for htdocs, but I am unable to change the permissions to save in the folder. 

I unlocked the root user, and tried the same thing, but it failed. I tried turning Lampp off, and trying again, and still it failed. 

ANY IDEAS?

---

### Post by Kareeser on 2009-05-02
You need to alter permissions to allow you to edit files. That could be as simple as changing ownership of /var/www/ to your account.

Please be advised that xampp might use a different file structure (as in, it might have installed itself to /opt). Doublecheck.

---

### Post by Dr Small on 2009-05-02
Yes, XAMPP is installed to /opt/lampp/

So, to the OP, you need to set the permissions on /opt/lampp/htdocs to 666 (rw-rw-rw):
```
sudo chmod -R 666 /opt/lampp/htdocs
```

---

### Post by kurtisnathan on 2009-05-02
Dr Small, I did what you did, to no avail. Kareeser, I don't know how to do whot you are suggesting.

---

### Post by Dr.Vista on 2009-05-02
> **kurtisnathan said:**
> Dr Small, I did what you did, to no avail. Kareeser, I don't know how to do whot you are suggesting.
Just paste that code in the terminal and hit enter. 

Edit: I didn't read your whole sentence. Disregard what I said. ;)

---

### Post by kurtisnathan on 2009-05-02
Nobody can help?

---

### Post by daboroe on 2009-05-02
if you are using xampp for live sites that is a big no no. just install everhything manually. it is very easy to set up. that is what i did.q

---

