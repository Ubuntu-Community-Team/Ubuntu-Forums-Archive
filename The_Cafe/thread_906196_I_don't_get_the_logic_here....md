---
title: "I don't get the logic here..."
date: 2008-08-31
forum: The Cafe
---

### Post by L815 on 2008-08-31
Hmm, I'm trying to figure it out... But I can't :confused::confused:

---

### Post by NovaAesa on 2008-08-31
Wow, that's confusing. Btw, I'm using the same (awesome) theme as you :P

---

### Post by Joeb454 on 2008-08-31
Very confusing ;) What theme is it that you're using?

---

### Post by pp. on 2008-08-31
Presumably, it's just a bug. The video runs with Flash Player 9. Unless, of course, they are afraid that people living in the future are looking at their broadcasts.

---

### Post by BlueSkyNIS on 2008-08-31
This happened to me many times...

---

### Post by L815 on 2008-08-31
The theme for those that requested is:
[http://gnome-look.org/content/show.php/Shiki-Colors?content=86717&PHPSESSID=68e99db4ca31b5ffecb56214122b4aae](http://gnome-look.org/content/show.php/Shiki-Colors?content=86717&PHPSESSID=68e99db4ca31b5ffecb56214122b4aae)

First time it happened to me. The message is what is making me fall out of my seat laughing (exaggerated of course)

---

### Post by NovaAesa on 2008-08-31
> **Joeb454 said:**
> Very confusing ;) What theme is it that you're using?
It's Shiki.

---

### Post by pp. on 2008-08-31
I just realised that OP asked about the logic of it all. From the message in the screenshot we see:

- The required version is 8
- The installed version is 10
- The program declares 10 to be less than 8

The program apparently compares the version identifications as strings instead of numbers. Since strings are compared from left to right, the program compares '8' with '1'. '1' is less than '8', hence '10' (as string) is less than '8'.

This kind of error is quite common.

---

### Post by Kingsley on 2008-08-31
I shot CNN an e-mail about that months ago. The response was they realize the issue and it'll be fixed soon...

---

### Post by JillSwift on 2008-08-31
> **Kingsley said:**
> I shot CNN an e-mail about that months ago. The response was they realize the issue and it'll be fixed soon...And so CNN's logic continues to astound. Unless they mean "soon" on a geologic time scale.

---

### Post by mike1234 on 2008-08-31
> **L815 said:**
> Hmm, I'm trying to figure it out... But I can't :confused::confused:


 Maybe because version 10 is still considered beta? Just a guess, I don't it's current status. Last time I downloaded it was.

M.

---

### Post by terabyte1 on 2008-08-31
What's hard with logic? 0 switches it off. 1 switches it on 

Now that's Binary! Speed it up and source it through a filter like a CPU and several thousand transistors (oh pardon me) Chips, feed it through your monitor and you got - zilch (Ahem!) You do have to switch on the monitor y'know?

Its wonderful how it works almost Black Magic really....:D


terabyte:lolflag:

---

### Post by Prefix100 on 2008-08-31
yeah I also have the latest version of flash installed but the zero7 site says I need to update :/

---

### Post by hyperhopper on 2008-08-31
> **pp. said:**
> Presumably, it's just a bug. The video runs with Flash Player 9. Unless, of course, they are afraid that people living in the future are looking at their broadcasts.

but then the people in the future could just get 8 or 9, OR they could just wait untill cnn fixed it to work for ten because they are in the future so they really wouldnt have to wait....

---

### Post by Mateo on 2008-08-31
> **pp. said:**
> I just realised that OP asked about the logic of it all. From the message in the screenshot we see:

- The required version is 8
- The installed version is 10
- The program declares 10 to be less than 8

The program apparently compares the version identifications as strings instead of numbers. Since strings are compared from left to right, the program compares '8' with '1'. '1' is less than '8', hence '10' (as string) is less than '8'.

This kind of error is quite common.

I doubt it's even that complex.  More likely I bet that it discovers that the installed version is not compatible with version 8 and assumes the installed version to be older.

---

### Post by pp. on 2008-09-01
> **Mateo said:**
> I doubt it's even that complex.  More likely I bet that it discovers that the installed version is not compatible with version 8 and assumes the installed version to be older.

I have version 9, and it accepts that. I presume that it accepts version 8 as well. Hence, the string comparison hypothesis would fit the available facts best, I think.

A great many software products produce strings when asked about their version IDs.

---

### Post by MaxIBoy on 2008-09-01
CTHUGA did the same thing, it said I needed to upgrade to D3D version 4.

---

