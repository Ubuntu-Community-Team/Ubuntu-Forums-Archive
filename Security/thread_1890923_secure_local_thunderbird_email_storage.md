---
title: "secure local thunderbird email storage?"
date: 2011-12-04
forum: Security
---

### Post by davidmaxwaterman on 2011-12-04
Hi,

I'm considering trying to store my local email in an secure way - ie so that 'the user' (ie me) has to authenticate him/herself before gaining access.

I use Thunderbird, so my first thought was to symlink the ~/.thunderbird directory into my ~/Private folder and follow the instructions to make that folder encrypted.

However, I figure that I am making it up as I go alone, and it seems sure to be something others have done and have a great solution for.

Is there a good solution to storing email securely?

Thanks,

Max.

---

### Post by Dangertux on 2011-12-04
I'm not an expert on POSIX linking however I don't think your solution would work. Here is my reasoning.

A symbolic link does NOT share the same inode, so if you symlinked them, then encrypted the symlinks the stored email would still be available unencrypted at the inode.  I would think you would need to hardlink them, and even then I don't think encrypting the hardlink would solve the issue. So what you really need to do is encrypt the actual data in the thunderbird directory.

Someone more knowledgeable on the subject feel free to correct this if it's wrong, but that is my understanding of the situation.

I hope this helps.

---

### Post by bluexrider on 2011-12-04
under account settings Local Folders you can denote where you want to store the mail. If it is an encrypted folder i am sure you would have to use permissions. although i've never tired the encrypted folder before.

---

### Post by davidmaxwaterman on 2011-12-04
> **Dangertux said:**
> I'm not an expert on POSIX linking however I don't think your solution would work. Here is my reasoning.

A symbolic link does NOT share the same inode, so if you symlinked them, then encrypted the symlinks the stored email would still be available unencrypted at the inode.  I would think you would need to hardlink them, and even then I don't think encrypting the hardlink would solve the issue. So what you really need to do is encrypt the actual data in the thunderbird directory.

Someone more knowledgeable on the subject feel free to correct this if it's wrong, but that is my understanding of the situation.

I hope this helps.

What I was imagining was a folder that I decrypt before even running Thunderbird. I'm "sure" TB will follow a symlink I put in ~/.thunderbird, so I just need to make sure I have decrypted the Private folder before running TB, then it would be none-the-wise and work just fine. The real data would be in ~/Private/.thunderbird, I suppose.

That's based on my experience from using encfs anyway...

---

### Post by DZ* on 2011-12-04
> **Dangertux said:**
> So what you really need to do is encrypt the actual data in the thunderbird directory.

I believe that is what he's proposing to do. The actual data is encrypted in ~/Private and ~/.thunderbird is just a symlink to it. When Private is unmounted, .thunderbird would point to a folder that contains encrypted data (or an empty one depending on the setup).

---

### Post by davidmaxwaterman on 2011-12-04
> **bluexrider said:**
> under account settings Local Folders you can denote where you want to store the mail. If it is an encrypted folder i am sure you would have to use permissions. although i've never tired the encrypted folder before.

Ah, using the local folder setting would remove the need for a symlink, so that's a non-issue, though easy enough anyway.

I don't understand your permissions comment. In my experience of using an encfs folder, you just need to enter a password and the folder suddenly has stuff in it....I think that's right, anyway...I guess I looked in the folder once while it wasn't encrypted, but I don't really remember. I always used cryptkeeper gui to access the encrypted folder I used to use.

So, I guess this isn't something someone has figured out an optimum solution for yet? Perhaps coming up with "one's" own solution is easy enough that no one has bothered?

---

### Post by davidmaxwaterman on 2011-12-04
> **DZ* said:**
> I believe that is what he's proposing to do. The actual data is encrypted in ~/Private and ~/.thunderbird is just a symlink to it. When Private is unmounted, .thunderbird would point to a folder that contains encrypted data (or an empty one depending on the setup).

Right, though that is important, I guess....it might be that running thunderbird without decrypting the data could risk corrupting it... I need to check that.

---

### Post by Dangertux on 2011-12-04
> **DZ* said:**
> I believe that is what he's proposing to do. The actual data is encrypted in ~/Private and ~/.thunderbird is just a symlink to it. When Private is unmounted, .thunderbird would point to a folder that contains encrypted data (or an empty one depending on the setup).

Okay I did it in reverse in my head. IE: store mail in .thunderbird and link ~/Private/.mail or some other to that as opposed to the other way around. I'm silly :-P

If this is the case then the above solution would be correct. Thanks for the clarification :-)

Also for OP if you use ecryptfs it should be decrypted at mount (login) so your mail would be plaintext while you're logged in but once logged out it would be encrypted. Just something to keep in mind.

---

### Post by DZ* on 2011-12-04
> **davidmaxwaterman said:**
> I use Thunderbird, so my first thought was to symlink the ~/.thunderbird directory into my ~/Private folder and follow the instructions to make that folder encrypted.

I use encfs and zenity for that kind of stuff. A panel launcher starts a bash script with a graphical password prompt utilizing zenity. ~/.thunderbird is a softlink to $HOME/Fuse/decr. "chmod 000" is a way to prevent thunderbird from making a bunch of "first time launch" files in decr if you start it without the script. 

Admittedly, this is not very polished. Use at your own risk!

Here is the script to launch thunderbird:
```
#!/bin/bash
bah=$(zenity --entry --hide-text --title="EncFS Password" --text="Type in password.")
chmod 755 $HOME/Fuse/decr
chmod 755 $HOME/Fuse/encr
echo $bah | encfs --stdinpass $HOME/Fuse/encr $HOME/Fuse/decr
if [ $? == 0 ]
then
   thunderbird
   sync
   fusermount -u $HOME/Fuse/decr
else
   zenity --title="mount failed" --info --text="bad password" 0x0
fi
chmod 000 $HOME/Fuse/decr

```
Here are possible commands to setup the encrypted thunderbird folder (assuming there are already data in ~/.thunderbird). I'd do a backup first.
```
sudo apt-get install encfs zenity
mkdir -p $HOME/Fuse/encr
mkdir -p $HOME/Fuse/decr
encfs $HOME/Fuse/encr $HOME/Fuse/decr
mv $HOME/.thunderbird $HOME/Fuse/decr
pushd $HOME; ln -s Fuse/decr/.thunderbird .thunderbird; popd
fusermount -u $HOME/Fuse/decr
chmod 000 $HOME/Fuse/decr
```

---

