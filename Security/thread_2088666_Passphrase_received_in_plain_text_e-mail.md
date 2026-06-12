---
title: "Passphrase received in plain text e-mail"
date: 2012-11-27
forum: Security
---

### Post by yeehi on 2012-11-27
A couple of organizations I know have web pages that automatically send you an e-mail when you sign up.

The e-mail includes your username and passphrase in plain text.

1) Is sending an e-mail with your passphrase like this always a bad policy? 

2) Can I deduce from this that the passphrases stored on their database are not hashed? 

3) Is it a sign that they have poor security?

4) Should I change my passphrase, if a similar one has been used on other sites, now that this one has been sent in plain text via email?

Thanks for your help!

---

### Post by mike acker on 2012-11-27
> **yeehi said:**
> A couple of organizations I know have web pages that automatically send you an e-mail when you sign up.

The e-mail includes your username and passphrase in plain text.

1) Is sending an e-mail with your passphrase like this always a bad policy? 

2) Can I deduce from this that the passphrases stored on their database are not hashed? 

3) Is it a sign that they have poor security?

4) Should I change my passphrase, if a similar one has been used on other sites, now that this one has been sent in plain text via email?

Thanks for your help!

it's a rather common practice, in my experience

i don't worry about it too much as generally you can change your password right after receiving the initial

done right the initial password should be 1 use only and limited to e.g. 10 minutes

~~~~~

in thinking about hackers it is critical to observe that most hacking is facilitated by the installation of malware, -- which I like to describe as "un-authorized programming" *

  recently there has been a very refreshing trend to the provision of "approved libraries" such as we have for Ubuntu.  I like to score this idea with 5 gold stars.

it is interesting to note that Google/Android is moving in this direction with their mobil app store library.  about time, I'd say.

one other thing that is important and that is not addressed is the **Software Inventory Audit**.  to start, the customer will need a manifest of the software that is supposed to be installed.  The list of binaries and the CRC for each would then be obtained from the OEMs and the computer's disk checked against this manifest.    the Audit would need to run from a live CD or better yet, automatically as an extension of UEFI.

if the software approval process has failed at any point the problem should then be detected.  there is a real opportunity for Canonical to get a Big Jump on the competition by producing this process.
~~~~~
* using an un-authorized update to your computer software the attacker can modify the behavior of your computer in real-time and this is generally how hackers do their dirty work.

it is important that the reader notice passwords and 2-factor authentication schems are of no use against these malware based attacks: the attacker uses your credentials while you are logged on to do his work.

just as though you were trying to drive a car with the steering dis-connected.

---

### Post by offgridguy on 2012-11-27
> **yeehi said:**
> A couple of organizations I know have web pages that automatically send you an e-mail when you sign up.

The e-mail includes your username and passphrase in plain text.

1) Is sending an e-mail with your passphrase like this always a bad policy? 

2) Can I deduce from this that the passphrases stored on their database are not hashed? 

3) Is it a sign that they have poor security?

4) Should I change my passphrase, if a similar one has been used on other sites, now that this one has been sent in plain text via email?

Thanks for your help!
I would take it as a sign of poor security.

---

### Post by DanR01 on 2012-11-27
Well, if you're going to change the passphrase to something else as soon as you get the email that's just about acceptable.

Unencypted email is like sending a postcard, anyone involved in any stage of its delivery can read it.

I don't think that you can deduce whether the password is hashed or not from the email you receive. Certainly storing passwords in plaintext is a very poor practice. Storing hashes passwords without using a salt is also not ideal.

---

### Post by OpSecShellshock on 2012-11-27
One way to determine if passwords aren't hashed is to see if there's a list of special characters you aren't allowed to use when choosing your own password. If they tend to function as operational characters in database queries that can be a pretty good indication that they are being passed in the clear.

---

### Post by Dave_L on 2012-11-29
> **yeehi said:**
> 4) Should I change my passphrase, if a similar one has been used on other sites, now that this one has been sent in plain text via email?

in my opinion, changing it would be a good idea.

But using the same pass phrase on multiple, unrelated sites is not a good thing to do.

---

### Post by Ms. Daisy on 2012-11-29
> 4) Should I change my passphrase, if a  similar one has been used on other sites, now that this one has been  sent in plain text via email?> **Dave_L said:**
> in my opinion, changing it would be a good idea.

But using the same pass phrase on multiple, unrelated sites is not a good thing to do.
+1000
Why would someone concerned about security use similar passwords anywhere?

---

### Post by SeijiSensei on 2012-11-29
Are you talking about sites where you get an email with an initial password upon signing up?  I don't have a problem with that practice since it's expected you'll replace the initial password with one of your own the first time you log in.  Sending you back a password you created in plain text is a serious security flaw in my mind.

And the fact that you received the password in plain text is not an indication that it is stored in plain text on the server.  I wrote a HIPAA-compliant application where everything the person enters is encrypted with AES256 before being stored in the database.  Since it's a symmetric cipher, I could easily decrypt the password and send it to you in plain text even though its encrypted on the server itself.

---

### Post by Dave_L on 2012-11-30
> And the fact that you received the password in plain text is not an indication that it is stored in plain text on the server.

I agree.

Discussion forum scripts I've used would email the user name and password (in plain text) upon initial registration and upon a "forgot password" request, even though the password was stored in the database using one-way encryption. At those times, the script momentarily "knows" the plain text password, even though it's subsequently encrypted; the original unencrypted password was not stored anywhere (although in theory it could wind up in server email logs). In the case of a "forgot password" request, a new, random password would be generated, emailed and then encrypted for storage in the database.

---

### Post by Ms. Daisy on 2012-11-30
Honestly I encountered the same thing with a few mailing lists and I thought it was odd. So they're handling the password correctly on their end, they email it to you and then it becomes YOUR responsibility to handle it correctly.

If it's a freemail account, then it's https, so it's encrypted.  But when it's in transit to your email server,  it's not encrypted, right?

It just seems weird and counter-intuitive to send a password in plain text. Ever.

---

### Post by Hungry Man on 2012-12-01
I would assume that if they have access to your plaintext password it means they aren't hashing it or they're doing something wrong.

---

### Post by SeijiSensei on 2012-12-01
As I said before, if the password is stored using a symmetric cipher like AES rather than as a one-way hash like MD5 or SHA1, it can be decrypted and sent to the user.

---

### Post by Ms. Daisy on 2012-12-01
> **SeijiSensei said:**
> As I said before, if the password is stored using a symmetric cipher like AES rather than as a one-way hash like MD5 or SHA1, it can be decrypted and sent to the user.
I guess I'm being dim. Are there instances where it's ok to send a user their plaintext password and others where it's not?  I get that they need to store it securely. But what about in transit? Plain text unencrypted traffic? If you send it out in plaintext, then it doesn't matter how securely you stored it on your servers. Anyone with wireshark can read the password. It makes no sense to me.

---

### Post by OpSecShellshock on 2012-12-01
For a lot of sites it's the only means they have of getting a new password to the user, and they do tend to suggest changing it immediately. It does carry risks in the event of interception, and it does sort of push those risks onto the user. I know that if I received a plain text password in an email I'd change it right away.

---

### Post by Ms. Daisy on 2012-12-01
> **OpSecShellshock said:**
> For a lot of sites it's the only means they have of getting a new password to the user, and they do tend to suggest changing it immediately. It does carry risks in the event of interception, and it does sort of push those risks onto the user. I know that if I received a plain text password in an email I'd change it right away.
True, except that the default for two (infosec) mailing lists is that they'll email your password once every 6 weeks or so. If it's a bad idea once, then it's a great idea repeatedly, right?...

Why don't they make you set your password on first login?  Or set the password yourself when you sign up for the mailing list. Why email the password at all?  I can't understand why a mailing lists full of infosec dorks would find this email method acceptable.

---

### Post by OpSecShellshock on 2012-12-01
Oh, I didn't realize you were talking about infosec lists! No, no, the stuff we come up with is for *other people* to do, not us.

---

### Post by Ms. Daisy on 2012-12-01
Lol - totally explains it!

---

### Post by SeijiSensei on 2012-12-01
> **Ms. Daisy said:**
> I guess I'm being dim. Are there instances where it's ok to send a user their plaintext password and others where it's not?

As a general rule, no it doesn't make any sense.  I had to write some code for password retrieval a while back.  We send them an email with a unique link that takes them back to the site and makes them answer the two security questions they chose at registration.  After all of this, I let them change their password.  

This was for a healthcare organization; HIPAA regulations would never let us send a person a password in plain text.  Hell, I can't even send the person an email telling her when her next physician's appointment is scheduled.  (Nosy boss reads email about employee's appointment, checks to see who the physician is, discovers the employee has cancer, and terminates the employee's contract on some trumped-up grounds or another.)  It bugs me when physicians hand out business cards with their email address on them.  Obviously they have no clue about why they cannot send patients plain-text emails.

---

