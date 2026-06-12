---
title: "Lightdm wallpaper uses user wallpaper?"
date: 2011-11-16
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by Glenn nl on 2011-11-16
Hello, I read the Lightdm wallpaper will use the users wallpaper.
But.. what happens when there are multiple users on one computer?

Thankts. :)

---

### Post by vikktor91 on 2011-11-16
[This]("http://www.youtube.com/watch?feature=player_embedded&v=seQ6C-yEpCw")

---

### Post by effenberg0x0 on 2011-11-16
Simple lightdm manager:
goo.gl/9AAYl

---

### Post by Starks on 2011-11-17
What if the user has a pornographic wallpaper?

---

### Post by kaldor on 2011-11-17
> **Starks said:**
> What if the user has a pornographic wallpaper?

Was just thinking that :)

Though in reality, I doubt anyone would use one if the PC was in use by other people.

---

### Post by effenberg0x0 on 2011-11-17
It is global indeed, as it is set at /etc/lightdm/unity-greeter.conf. 

```
[greeter]
background=/usr/share/backgrounds/warty-final-ubuntu.png

```

I think it is a wise workaround to just replace /etc/lightdm/unity-greeter.conf for a softlink pointing to $HOME/.config/lightdm/unity-greeter.conf to enforce per-user settings. Without putting any real thought into it, I think this should work:
```

for users in `ls /home`; do 
sudo mkdir -p /home/$users/.config/lightdm 
sudo cp /etc/lightdm/unity-greeter.conf /home/$users/.config/lightdm/unity-greeter.conf
sudo chown $users:root /home/$users/.config/lightdm -R
sudo chmod 750 /home/$users/.config/lightdm -R
done
sudo mv /etc/lightdm/unity-greeter.conf /etc/lightdm/unity-greeter.conf.backup
sudo ln -s /etc/lightdm/unity-greeter.conf ~/.config/lightdm/unity-greeter.conf

```[B]
OBS: [/B]I didn't had the time to look. But at this point I really thought they should already have done something like this by default. Or export the greeter path as an environment variable (it sure would be better and safer).

---

### Post by seeker5528 on 2011-11-17
> **Starks said:**
> What if the user has a pornographic wallpaper?

Everybody is OK with it or somebody is in for a shock.

> **kaldor said:**
> Was just thinking that :)

Though in reality, I doubt anyone would use one if the PC was in use by other people.

Silly wabbit. :P

Later, Seeker

---

### Post by Starks on 2011-11-17
[https://bugs.launchpad.net/unity-greeter/+bug/844081/](https://bugs.launchpad.net/unity-greeter/+bug/844081/)

Mark speaks (in response to my comment).

> On 17/11/11 11:30, Eric Appleman wrote:
> I agree with Fred and his waifu wallpaper.
>
> What if the background is NSFW or confidential?

Don't pick a wallpaper which can be viewed over your shoulder or when
you unlock a screen or plug into a projector that you are not
comfortable with your mother[-in-law] seeing.

Mark


Not everyone is agreeing with this on the grounds of security.

---

### Post by cariboo on 2011-11-17
I tend to agree with Mark, if your computer is an area of your home where your desktop is view-able by others, use a picture that is acceptable to your mother/wife/SO. Just because you can, doesn't mean you should.

---

### Post by Georgia boy on 2011-11-19
> **Starks said:**
> What if the user has a pornographic wallpaper?

Don't look Ethel!!!!!
:D

---

