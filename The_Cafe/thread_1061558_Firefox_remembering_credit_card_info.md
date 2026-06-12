---
title: "Firefox remembering credit card info"
date: 2009-02-05
forum: The Cafe
---

### Post by Polygon on 2009-02-05
I was just buying a song off of paypal, and i was shocked to find out that firefox had stored my credit card number / address / phone / expiration date / csc in its cache and when i was typing it in it prompted to fill it in for me (with the little drop down thingy)

i have cleared my cache since i found out, but I thought firefox would....not remember this kind of stuff, kinda like password fields......or is this a problem with the paypal site not properly set up?

either way, this is  a big security issue i think.

---

### Post by Grant A. on 2009-02-05
Isn't the stuff hashed anyways?

---

### Post by Polygon on 2009-02-05
is it? how does firefox determine what is sensitive credit card info and what is just some other random text field?

---

### Post by yabbadabbadont on 2009-02-05
It will remember **anything** you enter in a form if you have that option enabled.  As you said, it doesn't know what is being entered in a form, just that it is and you have the option set to remember it.  Turn it off if you don't want it to do so.  Edit->Preferences->Privacy->Remember what I enter in forms and the search bar.

---

### Post by Kvark on 2009-02-05
The website should have told the web browser to turn off auto complete for that form by adding the autocomplete="off" attribute to the <form> tag. It's not valid standard HTML but works in all major browsers.

The information may be stored encrypted by not hashed. The only way to know if a hashed value is "example" is to hash "example" and see if you end up with the same hash as the stored one. In other words hashed information can only be recovered with a brute force dictionary attack. If it's not salted you can quickly search for the stored hash in a dictionary of prehashed values. If it's salted (a random number was added to the information before hashing) you must hash a new dictionary with the same salt which takes a very long time. It's not reasonable to rely on a dictionary attack to retrieve information during normal usage so if stored information is retrieved you know it's not hashed.

---

