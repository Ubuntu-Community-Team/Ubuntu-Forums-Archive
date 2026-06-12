---
title: "trying out Opera browser-  found a password hasher..?"
date: 2007-03-08
forum: The Cafe
---

### Post by billdotson on 2007-03-08
it is a password hashing widget it has a input for the parameter the master password and then a button to hash the password.  What exactly do you do for parameter.. I know in Python in you do something like input(aParameter) aParameter represents one parameter.  Since a parameter is pretty much a variable in computer science what would you put into the parameter for this widget? 

So the point of a hasher is to have a master password but then for each individual account on a website or something it is actually a different password correct?

---

### Post by berserker on 2007-03-11
The parameter would be 'gmail' for your Google Mail account or 'ebay' for your eBay account or 'paypal' for your PayPal account, etc.

Then you use one master password for them all and different passwords are created depending on your parameter.  The advantage with this method is you just have to remember an obvious parameter name and one master password and the resulting hash will always be the same.  

If you're away from your computer then use [http://www.hashapass.com/index.html](http://www.hashapass.com/index.html) to regenerate the password for whatever account you need.

HTH

---

### Post by billdotson on 2007-03-15
oh ok.  I figured it out by using the hasher in Firefox before seeing it here.. thanks though

---

