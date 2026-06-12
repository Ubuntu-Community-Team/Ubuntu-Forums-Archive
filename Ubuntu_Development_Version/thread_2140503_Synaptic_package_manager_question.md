---
title: "Synaptic package manager question"
date: 2013-04-29
forum: Ubuntu Development Version
---

### Post by williejones on 2013-04-29
Anyone using synaptic who has changed the source list from Raring to Saucy?
I am getting updated and installing new packages with the Synaptic Package Manager, but when I select Settings > Repositories nothing comes up. 

If you have synaptic installed see what you get.

---

### Post by cariboo on 2013-04-29
This has been a common problem over the last several release when using this command:

```
sudo sed -i 's/raring/saucy/g' /etc/apt/sources.list
```

to update the repositories. Use the solution give in this [post]("http://ubuntuforums.org/showthread.php?t=2138987&p=12619169&viewfull=1#post12619169").

I plan on adding this to the Common Problems section of my siicky in the next couple of days.

---

### Post by williejones on 2013-04-29
I also just noticed Software Updater (which I do not use in development) clicking the settings does nothing.

---

### Post by williejones on 2013-04-29
> **cariboo907 said:**
> This has been a common problem over the last several release when using this command:

```
sudo sed -i 's/raring/saucy/g' /etc/apt/sources.list
```

to update the repositories. Use the solution give in this [post]("http://ubuntuforums.org/showthread.php?t=2138987&p=12619169&viewfull=1#post12619169").

I plan on adding this to the Common Problems section of my siicky in the next couple of days.

Thanks Cariboo907 this worked.  It took me a while to reply as there was a lot to edit.
By the way I also had Quantal, Precise etc in the file which i left alone.

By the way I do not see the "Solved" option to mark post as solved.

---

### Post by cariboo on 2013-04-29
To mark your thread solved, use this method:

> Go to the first post in your thread. Click on "Edit Post". Now click on the orange "Go Advanced" button. In the advanced editor change the prefix to "SOLVED". Now click on the orange "Save Changes" button.

---

### Post by williejones on 2013-04-29
> **cariboo907 said:**
> To mark your thread solved, use this method:

Thanks that was hard to find

---

### Post by williejones on 2013-04-30
I think I have found a better solution,
 reinstalling Reinstalled the following packages:
python-apt-common (0.8.8ubuntu6)
This seems to work as I had edited out raring for saucy and reinstallint the above put back raring.

---

### Post by cariboo on 2013-04-30
On my system /usr/share/python-apt/templates/Ubuntu.info, lists all the versions back to warty, I just left it the way it is, just added the new bit. This is a fresh install of Raring upgraded to Saucy.

---

### Post by ventrical on 2013-04-30
> **cariboo907 said:**
> This has been a common problem over the last several release when using this command:

```
sudo sed -i 's/raring/saucy/g' /etc/apt/sources.list
```

to update the repositories. Use the solution give in this [post]("http://ubuntuforums.org/showthread.php?t=2138987&p=12619169&viewfull=1#post12619169").

I plan on adding this to the Common Problems section of my siicky in the next couple of days.


Thanks .

 I forgot that one :)

---

### Post by mc4man on 2013-04-30
> **cariboo907 said:**
> 
to update the repositories. Use the solution give in this [post]("http://ubuntuforums.org/showthread.php?t=2138987&p=12619169&viewfull=1#post12619169").

I plan on adding this to the Common Problems section of my siicky in the next couple of days.
I would suggest not recommending the use of "sudo gedit ..." 
While not extremely bad, unlike the recent past  the sudo gedit command will now use the users config instead of roots so probably should be avoided.

---

### Post by cariboo on 2013-04-30
> **mc4man said:**
> I would suggest not recommending the use of "sudo gedit ..." 
While not extremely bad, unlike the recent past  the sudo gedit command will now use the users config instead of roots so probably should be avoided.

I only suggested sudo, as some users may not have installed gksu and changed the properties to use sudo instead of su.

---

