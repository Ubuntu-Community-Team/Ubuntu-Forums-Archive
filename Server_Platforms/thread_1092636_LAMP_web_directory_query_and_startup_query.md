---
title: "LAMP web directory query and startup query"
date: 2009-03-10
forum: Server Platforms
---

### Post by funkyali on 2009-03-10
Hi

I've just successfully installed and secured my LAMPP installation on my ubuntu 8.10 box.

I can see that the web folders seem to be pointing to /opt/lampp/htdocs. 

1. How can I create,edit,copy and delete in this folder as its owned by root?

2. How can I run sudo /opt/lampp/lampp start when my server starts up?

I am a home user and therefore I'm the only one that will most likely be using this folder. If its better to locate it to another folder then please advise me as I am a new ubuntu/linux user.

Many thanks for the excellant support that this forum provides.

---

### Post by hyper_ch on 2009-03-10
??? what did you install? by default the webroot is /var/www

---

### Post by funkyali on 2009-03-10
I followed this tutorial on how to install xamp for linux 
[http://www.apachefriends.org/en/xampp-linux.html#374](http://www.apachefriends.org/en/xampp-linux.html#374) 

You will see near the bottom it says 
/opt/lampp/htdocs/ 	The Apache DocumentRoot directory.

---

### Post by hyper_ch on 2009-03-10
I see... not the usual way I'd install it... however it you don't want to auto-start apache, mysql everytime it might not be as bad. As for your question, probably the simplest way would be to chown the document root to your username...

---

### Post by funkyali on 2009-03-10
How do I do that?

I know I have to run the following command in the terminal everytime I start at the moment

```
sudo /opt/lampp/lampp start
```

This command starts both apache and mysql together which I am happy with. I just need to find out how I can create,edit,delete within /opt/lampp/htdocs and how to start it up automatically with user interaction.

---

### Post by funkyali on 2009-03-11
I  have sorted out the my question 2.

I am just stuck on my first question now.

---

### Post by hyper_ch on 2009-03-11
> **funkyali said:**
> I  have sorted out the my question 2.

I am just stuck on my first question now.

> **hyper_ch said:**
> As for your question, probably the simplest way would be to chown the document root to your username...

:popcorn:

---

### Post by funkyali on 2009-03-11
Hi Hyper,

You'll see my response to original post. I'm not to sure how to chown the document root to my username. Could you help me? Is it best to leave it in the deaflut location or could I move it?

---

### Post by hyper_ch on 2009-03-11
> **funkyali said:**
> I'm not to sure how to chown the document root to my username.

what did you do to find out more about "chown"?

---

### Post by funkyali on 2009-03-11
I googled it and then tried the following 
```
sudo chown root.mygroup /opt/lampp/htdocs
```

This did not work.

---

### Post by funkyali on 2009-03-11
Not to worry I sorted it out 

sudo chown -hR username:usergroup /opt/lampp/htdocs/

---

### Post by iyas120 on 2009-03-13
Follow this tutorial might help:
[http://www.apachefriends.org/f/viewtopic.php?f=17&t=32164](http://www.apachefriends.org/f/viewtopic.php?f=17&t=32164)

---

