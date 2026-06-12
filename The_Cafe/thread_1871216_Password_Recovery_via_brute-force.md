---
title: "Password Recovery via brute-force"
date: 2011-10-28
forum: The Cafe
---

### Post by alphaamanitin on 2011-10-28
Okay, please actually read my post here, not just assume I want help hacking into some one's files.  I have a keepassX database that I can remember basically ALL of the password, but I cannot access my database.  I am trying to look into a script or something that will help me make variations on my password.  It is a beast of a password, something like 65 characters long.  I have narrowed it down to basically three to five variable positions, but it could be more.  Is there something available in helping me test different password variations, or should I just make a list by hand and check?

The only thing I would like is my bank password, but I can call and have them reset it, otherwise it is fine if it I never recover I guess.  Anyway, I am sure it is NOT a damages file due to keeping the file in dropbox, because I also have a back up on my desktop and I cannot open that one either.  Also, does anyone know if there is a way to find the hash of your password in the keepassX files?  I mean it has to be there somewhere and it cannot be encrypted because it has to be used as a hash check.  I thought it might be faster for me to make a large list of possible passwords, hash it, and check those hashes.

Thanks,

AlphaA

---

### Post by markp1989 on 2011-10-28
> **alphaamanitin said:**
> Okay, please actually read my post here, not just assume I want help hacking into some one's files.  I have a keepassX database that I can remember basically ALL of the password, but I cannot access my database.  I am trying to look into a script or something that will help me make variations on my password.  It is a beast of a password, something like 65 characters long.  I have narrowed it down to basically three to five variable positions, but it could be more.  Is there something available in helping me test different password variations, or should I just make a list by hand and check?

The only thing I would like is my bank password, but I can call and have them reset it, otherwise it is fine if it I never recover I guess.  Anyway, I am sure it is NOT a damages file due to keeping the file in dropbox, because I also have a back up on my desktop and I cannot open that one either.  Also, does anyone know if there is a way to find the hash of your password in the keepassX files?  I mean it has to be there somewhere and it cannot be encrypted because it has to be used as a hash check.  I thought it might be faster for me to make a large list of possible passwords, hash it, and check those hashes.

Thanks,

AlphaA

I don't see much hope in brute forcing it, if the password is 65 digits long,even if only using lower case letters there are  26^65 = 9.40302559×10^91 possible combinations.

edit: just read this,[http://superuser.com/questions/187885/keepass-lost-password-and-or-corruption-due-to-dropbox-keepassx](http://superuser.com/questions/187885/keepass-lost-password-and-or-corruption-due-to-dropbox-keepassx) sounts similar to your problem. using dropbox and not being able to log in.

---

### Post by alphaamanitin on 2011-10-28
> **markp1989 said:**
> I don't see much hope in brute forcing it, if the password is 65 digits long,even if only using lower case letters there are  26^65 = 9.40302559×10^91 possible combinations.

edit: just read this,[http://superuser.com/questions/187885/keepass-lost-password-and-or-corruption-due-to-dropbox-keepassx](http://superuser.com/questions/187885/keepass-lost-password-and-or-corruption-due-to-dropbox-keepassx) sounts similar to your problem. using dropbox and not being able to log in.

I don't think you read the entire post.  Yes the password is huge, but I am only looking at a few positions of error, the rest I KNOW are correct.  Also, since the back-up, which has never been on dropbox, will not open it must be the password.  I read that superuser and it was not any help for my situation.  Sadly, the keepassx forums are apparently dead, though I did make a post there as well.  Thanks for reading and posting though.  

AlphaA

---

### Post by CharlesA on 2011-10-28
I don't know of any way to find the hash of a the password used to access the keepass db. Might try posting over on their site, but I doubt you'd be able to get access to it unless you have a good backup of it.

In any case, if the password is that long, I highly doubt you'd be able to crack it - even if you are just replacing one or two characters.

---

### Post by alphaamanitin on 2011-10-28
> **CharlesA said:**
> I don't know of any way to find the hash of a the password used to access the keepass db. Might try posting over on their site, but I doubt you'd be able to get access to it unless you have a good backup of it.

In any case, if the password is that long, I highly doubt you'd be able to crack it - even if you are just replacing one or two characters.


Yeah, their site is pretty much dead.  Anyway, I don't understand why you say that I will have a hard time cracking it.  If I understand the mathematics of passwords correctly knowing the character in X position essentially means that said position no longer counts in the attempts to brute force it.  EG, if I have a 1,000 character password and know all but two of the characters I only need to test two passwords.  So in my instance I only have, from my knowledge of what is the uncertain positions in my password, a maximum of 50 or so possibilities.  

Anyway, I was really hoping some one knew how to find the hash, I'll just have to make a list of all the variable passwords I can think of and test them one by one on the back up.  

Thanks,

AlphaA

---

### Post by CharlesA on 2011-10-28
> **alphaamanitin said:**
> 
Anyway, I was really hoping some one knew how to find the hash, I'll just have to make a list of all the variable passwords I can think of and test them one by one on the back up.  


Good luck.

---

### Post by koenn on 2011-10-28
> **alphaamanitin said:**
>  EG, if I have a 1,000 character password and know all but two of the characters I only need to test two passwords.  
er, no, you'd need to test 26x26 paswords, assuming you know the missing characters are lowercase characters.  it blows up to 52x52 for lower or uppercase, 62x62 to include  numbers, and so on

if there's 1 character in your 1000 char string that you don't remember, you have to try all letters of the alphabet, that's 26 possibilities (or 52 or 62 etc). 

If there's 2 positions you don't know, you need try 26 chars on the 1st position, and for every char on the 1st position, you need to try all 26 chars on the 2nd position. Hence 26x26. or 52x52, and so on

for 3 missing chars -> 26x26x26, and so on

but it's fairly easy to write a script   that lists those combinations. 
Sometimes it's also fairly easy to pipe that list into a password prompt. 


say you have AAA?BBB?CCC and you know the question marks can be any of A,B or C, you'd go something like
```

for c1 in A B C; do
    for  c2 in A B C ; do

          echo AAA${c1}BBB${c2}CCC 

    done
done

```

that's your list

---

### Post by alphaamanitin on 2011-10-28
Ah yes, sorry the thoughts of my password slipped into my example.  Mine is more of this character is either lowercase or uppercase, this character is either a space or this, etc.  I am not in the I don't have a clue what this is, I'll have to test all characters range.  

And THANK YOU very much for that nice way of making a list of my possible passwords.

AlphaA

---

### Post by ki4jgt on 2011-10-28
> **alphaamanitin said:**
> Okay, please actually read my post here, not just assume I want help hacking into some one's files.  I have a keepassX database that I can remember basically ALL of the password, but I cannot access my database.  I am trying to look into a script or something that will help me make variations on my password.  It is a beast of a password, something like 65 characters long.  I have narrowed it down to basically three to five variable positions, but it could be more.  Is there something available in helping me test different password variations, or should I just make a list by hand and check?

The only thing I would like is my bank password, but I can call and have them reset it, otherwise it is fine if it I never recover I guess.  Anyway, I am sure it is NOT a damages file due to keeping the file in dropbox, because I also have a back up on my desktop and I cannot open that one either.  Also, does anyone know if there is a way to find the hash of your password in the keepassX files?  I mean it has to be there somewhere and it cannot be encrypted because it has to be used as a hash check.  I thought it might be faster for me to make a large list of possible passwords, hash it, and check those hashes.

Thanks,

AlphaA

I don't have an answer (the question/post is marked solved) but I would think that this idea would be condoned in the Linux community (not condemned). I've read this same request on other forums where the OP was literally called horrible names and accused of everything under the Sun. Don't be afraid to ask questions like this. Linux is about exploring not only the securities of your system, but also about exploiting it's vulnerabilities too. Although morally, most people are obligated to tell you to buzz off when you're asking to do something illegal. No one should assume (unless you give them reason to do so) that you want to do anything else with your intentions then what you have stated.
I'm actually glad that this community has responded with the information they did, instead of automatically assuming you to be trying to hack someone's information (like a few other forums I've visited where OPs have asked this same exact question).

---

### Post by alphaamanitin on 2011-10-28
I marked it as solved because I am confident that the above responses have given my as much help as I could possibly receive.  I agree with what you have said to the fullest extent.  People need to understand that these things happen.  The reason I don't write down the password is because that renders the password pointless.  Anyway, I am hoping that after a few days or week muscle memory will have me type the password in correctly.  

AlphaA

---

