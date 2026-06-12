---
title: "Help with a program"
date: 2012-02-25
forum: The Cafe
---

### Post by Triblaze on 2012-02-25
So on another site I go to, we have member's updates. It's pretty much a list of all the users, along with their post count and follow count and stuff like that, along with the increases from last week. There's also some community sections. It's kind of like a board newsletter. Anyway, the stat part is done with a script. Well, two actually. One has you enter the user's usernames into it, and it returns all their posting info (this script is hosted online by one of the users but is not built into the boards). The other script takes all the data and puts it in list form and totals up the increases and decreases.

Now, we recently moved to a new board system. So while the list that puts the data into a fancy format remains, the script for gathering the data no longer works because all the data is in a completely different place. The user who wrote it originally did it a long time ago and isn't here any more, I think.

So I figured I'd try to make one. I don't need to redo the second script, that still works because the data is input by the user, and I could code that myself if needed.

However, I don't really know anything about making code work with the web. So what I'm asking is, what do you use to gather data from a website? Optimally it'd look up the profiles based on the username and grab the data from there. How do I do that? Would you have it open the pages somehow and then grep it? Is there a specific online-grep sort of code?
I'm just wondering how I'd go about this, a few google searches haven't been especially helpful.

Answers in terms of Java would be appreciated, but I can try to work it out from anything really.

---

### Post by grahammechanical on 2012-02-25
Like you say it is a script. So, you can edit it in Gedit or a web site editor program like Bluefish.

You need to change the paths to the new paths. Try opening the script in Gedit to see how it works.

Regards.

---

### Post by baumanno on 2012-02-25
Well if it's a board system, chances are up you're dealing with a PHP/MySQL environment, which makes it a piece of cake really. Just search for some tutorials on that and you'll be rewarded with a plethora of results. But to get an idea, as grahammechanical suggested, why not check out the old script first to see what they had going on there before (supposing you have access to that).

Hugs

EDIT:
Not done this for some time, but you'd be looking for something along the lines of 
```

SELECT * FROM users WHERE postcount > 10

```
for example, to retrieve all users who have more than 10 posts

---

### Post by Triblaze on 2012-02-25
> **grahammechanical said:**
> Like you say it is a script. So, you can edit it in Gedit or a web site editor program like Bluefish.

You need to change the paths to the new paths. Try opening the script in Gedit to see how it works.

Regards.
The script is hosted online and the code isn't publicly visible.
> **baumanno said:**
> 
EDIT:
Not done this for some time, but you'd be looking for something along the lines of 
```

SELECT * FROM users WHERE postcount > 10

```for example, to retrieve all users who have more than 10 posts
I don't really know any SQL stuff (never really done online stuff), but  for a variable like postcount, wouldn't I have to have access to the  board's admin stuff or something? I mean, we can view the post counts,  but wouldn't the variable that stores that be on their filesystem and  then it just prints the end result to us? So looking up a variable from  the user end wouldn't work? Or am I just misinterpreting how this works?

And I tried using a combination of wget and grep in a bash script, with  mixed results. It kind of worked, but was somewhat inefficient.

---

### Post by alphacrucis2 on 2012-02-25
As you surmise, the SQL query is useless to you on a client side script. That poster probably thought you were talking about a server side script which can have direct access to the database. Your best bet however is to look at the source of the original script and try and adapt it to the layout and available functions of the new board.

---

