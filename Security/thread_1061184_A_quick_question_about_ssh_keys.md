---
title: "A quick question about ssh keys"
date: 2009-02-05
forum: Security
---

### Post by jerome1232 on 2009-02-05
Okay so I'm going to convert my ssh box's to only accept ssh keys, no passwords. I've got the accounts setup, I've got the private keys exported to a little fat16 thumbdrive so I can use them in other computers, the question is:

My keys have passphrases on them, does this mean that the private key is encrypted? So I don't need to encrypt the thumbdrive?

(I mean in order to import the key to any tool (like puttygen) it requests the passphrase for the key so I think they are encrypted I'm just making sure.)

---

### Post by e1mer on 2009-02-05
While it is better than no password, the key is just as
vulnerable to dictionary attack as the password on it.

It's better to get the key as needed via some auth method than
to use the thumbdrive.

EG: a password protected web page on the host.  You get the
key from the server by logging in by http, then you can get the
key on the new host and use it.

Give your key an unusual and scary name, obfuscate your form,
and try to make anyone suspicious of even wanting to log in.

This might make a great index.html to deliver an ssh key:
```

<html><head><title>Homeland Security Keystroke Logger</title></head>
<body>
  <?php 
  if( $_REQUEST['user'] == 'myuser'  
   && $_REQUEST['pass'] == 'amanaplanacanalpanama-palindrome' )
  { echo "<a href='FilenameNobodyCanGuessGoodTimesVirus.hoax'>
     Download A Worm</a.>";
  }
  ?>
   <form> Username: <input type=text name='password'>
         <br> Password: <input type=text name='user'>
         <br> <input type=submit name='go' value='infect me'>
   </form>
  </body>
</html>
   
```

---

### Post by jerome1232 on 2009-02-05
While I like your idea the reason I want to use keys is because someone has to physically steal my thumbdrive to get them, and then I can just ssh in to the server since the keys are stored on my desktop as well as the thumbdrive and make it not accept those keys anymore before they could ever brute force a good passphrase. 

I'm not sure if I like making them downloadable via a service that can be brute forced as well, although they would have to brute force the download service and then brute force the passphrase on the key.

At any rate I think you answered my question, the keys are encrypted when they have a passphrase set on them.

---

### Post by Dr Small on 2009-02-05
> **jerome1232 said:**
> At any rate I think you answered my question, the keys are encrypted when they have a passphrase set on them.

Of course. The attacker can steal your thumbdrive and take the key, but so long as you set a passphrase on the key he can't use it until he cracks the password. And depending on how difficult your password is to crack, it could take him a long time if ever.

---

### Post by hyper_ch on 2009-02-06
or you create a truecrypt container on the the thumbdrive and store the keys in there.

---

