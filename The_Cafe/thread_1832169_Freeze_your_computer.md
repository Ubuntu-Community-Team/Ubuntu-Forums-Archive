---
title: "Freeze your computer"
date: 2011-08-24
forum: The Cafe
---

### Post by Purplerob on 2011-08-24
I accidentally made an application that freezes my computer. So I made it into freezer. It freezes my computer but I don't know if it will work on all computers. Can some people please test it for me? 


FYI: You have to give yourself permission to execute the file 

Use with caution because it might work.

[IMG]http://ubuntuone.com/p/1CXr/[/IMG]

Download link:<snip>

---

### Post by Basher101 on 2011-08-24
why not test it in VirtualBox?

---

### Post by aaaantoine on 2011-08-24
No, thanks.  I prefer my computer to keep running.  And by elevating privileges, all bets are off.

Edit: Once I saw it was a Python script I decided to download it and review the code.  I'm no Python expert.  What is it actually doing?

---

### Post by Purplerob on 2011-08-24
it doesn't ask for your root password don't worry. All it does is create an infinite amount of windows all at once. I tested it on my computer and it works but my computer isn't very top of the line.

lol I don't know python either I was just trying out illumination software creator

---

### Post by SavageWolf on 2011-08-24
A fork bomb. Would going into a tty and killing all python work? Or xkill?

---

### Post by Bachstelze on 2011-08-24
> **aaaantoine said:**
> No, thanks.  I prefer my computer to keep running.  And by elevating privileges, all bets are off.

Edit: Once I saw it was a Python script I decided to download it and review the code.  I'm no Python expert.  What is it actually doing?

Basically when you click the button it calls a function that calls another function that cals the first function again, ad infinitum. What I'm wondering is why you don't get a recursion depth exception...

---

### Post by Purplerob on 2011-08-24
You could probably kill it somehow. Can someone just try it???

---

### Post by dniMretsaM on 2011-08-24
> **aaaantoine said:**
> No, thanks.  I prefer my computer to keep running.  And by elevating privileges, all bets are off.

I don't think he's saying you have to elevate privileges, he's saying you have to give it execute permissions (chmod +x or however you prefer to change permissions).

---

### Post by cgroza on 2011-08-24
> **Bachstelze said:**
> Basically when you click the button it calls a function that calls another function that cals the first function again, ad infinitum. What I'm wondering is why you don't get a recursion depth exception...
The default python depth is 1000. Maybe it just freezes and never reaches the limit.

---

### Post by cariboo on 2011-08-24
Removed link, and closing the thread, as we don't support this type of activity.

---

