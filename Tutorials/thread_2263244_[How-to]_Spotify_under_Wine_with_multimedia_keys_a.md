---
title: "[How-to] Spotify under Wine with multimedia keys and OSD"
date: 2015-01-30
forum: Tutorials
---

### Post by Maxim_Buur on 2015-01-30
[SIZE=2]Hi,

After some experimentation, and Spotify-notify (a project on GitHub) having failed me, I found out how to do the following:

1. Control (Next, previous, play/pause) Spotify.exe (running under Wine) with any keys on your keyboard
2. Show the title and artist information of the song switched to in a Ubuntu notification bubble (notify-osd)

This is awesome, because it makes Spotify running under Wine (the best Spotify solution currently available for Linux in my opinion) that more useful, and it feels super native!

Screenshot: [http://imgur.com/Y4laM5F](http://imgur.com/Y4laM5F)

I own an Acer C720 Chromebook running Xubuntu 14.10. I remapped my keys a while ago using this guide:
[http://www.reddit.com/r/chrubuntu/comments/1rsxkd/list_of_fixes_for_xubuntu_1310_on_the_acer_c720/ce2ej5y](http://www.reddit.com/r/chrubuntu/comments/1rsxkd/list_of_fixes_for_xubuntu_1310_on_the_acer_c720/ce2ej5y)

**The guide:**

1. Run this in terminal: ```
sudo apt-get install xbindkeys xdotool
```

2. Download spotify_cmd from this link: [https://code.google.com/p/spotifycmd/](https://code.google.com/p/spotifycmd/)

3. Put the contents of the .zip (spotify_cmd.exe and spotify_cmd.exe.so) in your home folder.

4. Decide which keys you want to use for 1. Next song, 2. Previous song and 3. Play/pause. (In my case I remapped my F1 key to Greek_NU with xmodmap because F1 already does something in Spotify and Chrome, which I found annoying. I then decided to use Greek_NU for previous song, F2 for next song, and F5 for play/pause)

5. Run the following command: ```
sudo gedit ~/.xbindkeysrc
```

6. Paste these lines in the file:
```
"xdotool keyup [COLOR=#ff0000]Greek_NU[/COLOR]; ./spotify_cmd.exe prev; notify-send -i [COLOR=#0000ff]/usr/share/icons/Numix-Circle/48x48/apps/spotify.svg[/COLOR] "Now playing" "`./spotify_cmd.exe status | tail -n +2 | head -1` - `./spotify_cmd.exe status | tail -n +3 | head -2`"  --urgency=critical --expire-time=1500"
[COLOR=#ff0000]Greek_NU[/COLOR]
"xdotool keyup [COLOR=#ff0000]F2[/COLOR]; ./spotify_cmd.exe next; notify-send -i [COLOR=#0000ff]/usr/share/icons/Numix-Circle/48x48/apps/spotify.svg[/COLOR] "Now playing" "`./spotify_cmd.exe status | tail -n +2 | head -1` - `./spotify_cmd.exe status | tail -n +3 | head -2`" --urgency=critical --expire-time=1500"
[COLOR=#ff0000]F2[/COLOR]
"xdotool keyup [COLOR=#ff0000]F5[/COLOR]; ./spotify_cmd.exe playpause; notify-send -i [COLOR=#0000ff]/usr/share/icons/Numix-Circle/48x48/apps/spotify.svg[/COLOR] "Play/pause" --expire-time=1000"
[COLOR=#ff0000]F5[/COLOR]
```

7. Replace the key symbol names ([COLOR=#ff0000]in red[/COLOR]) with the keys you want to use. A list of key symbol names can be found here: [http://wiki.linuxquestions.org/wiki/List_of_Keysyms_Recognised_by_Xmodmap](http://wiki.linuxquestions.org/wiki/List_of_Keysyms_Recognised_by_Xmodmap)

8. Replace the lines [COLOR=#0000ff]in blue [/COLOR][COLOR=#000000]with paths leading to the Spotify icon you want to use. (I use the one from the Numix Circle icon theme)

9. Now run: 
```
killall xbindkeys
xbindkeys &
```

It should work now! Run Spotify (running under Wine) and check it out!

Remember, you can be creative with the lines. To give you a start, what my Greek_NU key does is basically run '[/COLOR]./spotify_cmd.exe prev' to skip to the previous song. "Now playing" is the title of the notification bubble. (You can change this or remove it altogether) Then `./spotify_cmd.exe status | tail -n +2 | head -1` is a command which fetches the artist name from spotify_cmd.exe, and `./spotify_cmd.exe status | tail -n +3 | head -2` fetches the song title. '--expire-time=1500' means  that the notification bubble will be displayed for a 1500 milliseconds. The Google Code spotifycmd website lists more commands you could potentially use.

[B]Edit: Found a way to have cover art in the notifications as well
[/B]
1. Download spotify_buttons.zip: [http://www66.zippyshare.com/v/eRZZnYkB/file.html](http://www66.zippyshare.com/v/eRZZnYkB/file.html)

2. Extract [/SIZE]spotify_buttons.zip into your home directory.

[SIZE=2]3. Bind your keys to '[/SIZE]bash ~/spotify_buttons/previoustrack.sh', 'bash ~/spotify_buttons/nexttrack.sh', and 'bash ~/spotify_buttons/playpause.sh'.[SIZE=2]

4. Have fun, it looks and works awesome!

(This works by sending artist+title+'cover' to Google and downloading the first square jpg image)


Have fun with it and don't hesitate to ask me questions![/SIZE]

---

