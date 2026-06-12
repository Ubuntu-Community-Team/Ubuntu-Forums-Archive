---
title: "print spool security risk?"
date: 2013-08-21
forum: Security
---

### Post by Tom_ZeCat on 2013-08-21
I met a man who worked for law enforcement.  He was working on getting evidence from a Windows PC that belonged to an alleged criminal.  The owner had carefully wiped data and the cop wasn't finding anything.  However, then he looked at something the guy didn't think of: the print spool.  It revealed he had printed mailing labels to the address that had been bombed.  This lead to other evidence and he was busted.  

Fast forward to me.  I'm using Kubuntu.  I have no need to hide any criminal activity, but I do wonder if Kubuntu has a print spool that could end up being a security risk.  For example, maybe you type up in LibreOffice Writer a page of all your important passwords and print it without saving it and then keep it in your safe.  Even if you use a tool like KeepPassX, you might want some kind of hard copy of your passwords in a safe.  Then if a crook steals your laptop or somehow gain access to it, he looks at the print spool to find the password page you printed up, and, voilà!  He's got all the info he needs.  

Whatever you print up in Windows can be found and looked at unless you find some way to securely wipe the print spool.  Is the same true of *buntu?

---

### Post by Cheesemill on 2013-08-21
Just to add, most modern business-grade printers keep a copy of all recently printed documents on their internal memory so they can be easily printed again.

Th print spool in Linux is usually found at /var/spool/cups, I'm not sure if and how often it is cleared though. If you're really paranoid you could set up a cron job or manually delete the spool files after every print.

---

### Post by Tom_ZeCat on 2013-08-21
> **Cheesemill said:**
> Just to add, most modern business-grade printers keep a copy of all recently printed documents on their internal memory so they can be easily printed again.

Th print spool in Linux is usually found at /var/spool/cups, I'm not sure if and how often it is cleared though. If you're really paranoid you could set up a cron job or manually delete the spool files after every print.

Thanks.  I went into that directory and found the page of my passwords.  I shredded it with Bleachbit.  

When I installed Kubuntu, I chose the option of not encrypting my files.  Maybe I should change.  Would doing that have kept the print spool files encrypted?  
I guess I could just periodically go in with Bleachbit and shred them.  Next I should check if my printer holds documents.  I'd doubt it.  It's just a home-use small laser printer.  

This is good information.  Thanks.  It's also another possible way of retrieving a deleted file.

---

### Post by Cheesemill on 2013-08-21
> **Tom_ZeCat said:**
> When I installed Kubuntu, I chose the option of not encrypting my files.  Maybe I should change.  Would doing that have kept the print spool files encrypted?

That depends on the encryption method you choose. Ubuntu offers 2 different encryption types during installation, full-disk encryption and home folder encryption. Of these only full-disk encryption would encrypt the print spooler files as they live outside your home folder.

---

### Post by Tom_ZeCat on 2013-08-21
> **Cheesemill said:**
> That depends on the encryption method you choose. Ubuntu offers 2 different encryption types during installation, full-disk encryption and home folder encryption. Of these only full-disk encryption would encrypt the print spooler files as they live outside your home folder.

Does the full encryption significantly slow the PC down?  Seems like a decent option if it doesn't.  Otherwise, it's not that hard to shred the files with Bleachbit.  Can this encryption be turned on after installation.  I use TrueCrypt to encrpyt my important files, which is why I didn't bother to have encryption turned on during install.  Most of my files aren't sensitive.  I'd doubt a would-be criminal would be interested in my recipe for Eggplant Scallopini (and if he were, he could just ask for it).  But I keep a few spreadsheets with financial data encrypted.  

Edit: 
I realized it wasn't fair to mention my Eggplant Scallopini and make people all hungry.  Here's my recipe:  

Eggplant Scallopini

2 to 3 Tblsp olive oil
2 cupps chopped onion
2 bay leaves
6 cups diced eggplant (about 1 large eggplant)
2 medium-sized bell peppers, diced
1 lbs mushrooms, chopped
2 tsp salt
2 tsp dried basil
1/2 cup dry sherry (you can omit this but it just won't be the same)
3 to 4 medium-sized ripe tomatoes, chopped (I've used canned diced 
tomatoes drained and it was very good)
black pepper, to taste
8 to 10 medium cloves garlic, minced (great exercise when you're 
feeling stressed)
1 lb. pasta -- any shape
finely minced parsley

Heat the olive oil in a deep skillet. Add onion and bay leaves, and sauté over medium heat until the onions are soft (5 to 8 minutes). 

Add eggplant, peppers, mushrooms, salt, and basil. Cover and cook until the eggplant is tender (10 to 15 minutes), stirring occasionally.

Add wine, tomatoes, and black pepper. Simmer 10 to 15 minutes uncovered (the liquid will reduce). Stir in the garlic during the last 5 minutes. Meanwhile cook the pasta.Drain the pasta, toss with a little additional olive oil, and ladle the eggplant on top. Sprinkle with parsley and serve...

---

### Post by Cheesemill on 2013-08-21
I've used full-disk encryption on several machines and the speed penalty hasn't been noticeable (I think it's around the 5% mark).

Any half decent machine should run with it no problem, new CPU's that have the AES instruction set built-in shouldn't really take a hit at all. Unfortunately FDE is best set up during installation, there's no way to easily set it up afterwards.

PS - Thanks for the recipe, I've got a few aubergines growing in the greenhouse at the moment :)

---

