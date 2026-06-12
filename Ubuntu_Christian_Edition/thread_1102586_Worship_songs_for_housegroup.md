---
title: "Worship songs for housegroup"
date: 2009-03-21
forum: Ubuntu Christian Edition
---

### Post by nitep on 2009-03-21
Hi,
I have around 100 worship songs in mp3 saved on a data CD with 10 folders and 10 songs per folder.

Using my DVD player and TV I can rapidly get to and play any of these worship songs during home group worship time. It works very well.

I would like to be able to do the same thing but showing the lyrics on screen as the music is played.

Any ideas. I have tried this in Avidemux and also QDVDAuthor but had no success. The lyrics for each song I saved in JPEG form for those applications.

Thanks in anticipation

---

### Post by nitep on 2009-03-26
I have finally figured it out myself and now have a DVD that will play on any standard DVD player with the lyrics on screen and audio.
If anyone is interested I will give the details.

I have put a slightly improved tutorial on my website at [http://universe.witnesstoday.org/](http://universe.witnesstoday.org/)

I now have a much improved tutorial here

[http://ubuntuforums.org/showthread.php?p=7814987#post7814987](http://ubuntuforums.org/showthread.php?p=7814987#post7814987)

---

### Post by chuckn on 2009-03-26
> If anyone is interested I will give the details. 

I would like to know how you did that.

Thanks
Chuck

---

### Post by nitep on 2009-03-30
Hi Chuck

Well it is very time consuming but worth it to have worship songs for a home group.
I used QDVDAuthor to produce the DVD. I found a good tutorial at 
[http://qdvdauthor.sourceforge.net/guide](http://qdvdauthor.sourceforge.net/guide)
However the menus and windows did not quite match up with the version of QDVDAuthor that I have but it is still very good.

1. Get the songs you want from your CD's
2. Convert them to mp3.  I used Sound Converter
3. Next we need the lyrics in image form

I will first describe what is required for a one screen song.

4. Get the lyrics from the net or type them up your self.
5 . Use OpenOfficeDraw to create a textbox to paste one song in and enlarge the font as much as will fit on the  TV screen. In my first attempt the lyrics were way off the screen. I discovered that you can turn on a red dotted rectangle in QDVDAuthor showing the edge of the TV screen but even using that the text went off the TV screen. In OpenOfficeDraw I created a textbox with a blackborder around it using 4 black filled rectangles. After some experimenting you will have it the correct size and save for future use. You can have a pretty background to it. To save the image deselect then select all, under files-->export make sure the Selection box is checked (otherwise blank screen below your textbox becomes part of the image) and save the image. I used jpeg 90% to give 50 to 100kB image files. This image is used thousands of times to make the video so dont have it to big.
6. Now to create a .VOB file of a song with QDVDAuthor. Start a new project.
7. Click on DVDAuthor tab then add menu
8. Click on the add background button at the top and get your lyrics image. Convert it to PAL or NTSC scaled as required for your TV.
9. Right click on SubMenu 1 and click on Properties
10 . Click on the audio tab and then click on Add
11. Select your mp3 song then click on the Geometry tab and change the ending at: time from 1 second to  what it should be (It is show in purple at the top left or Play the song with Movie Player and it shows you the length)  and click on Accept.
12. You are now ready to generate the .VOB by clicking on the Create DVD button at the top. Then click on OK in the Command Queue window. It will take a very long time.
13. When finished you will find a  VTS_01_0.VOB    file in  the VIDEO_TS folder where you directed the projects output at step 6  . Rename it and copy it to your video folder. These are the video clips that make up the DVD when they are all ready. You can play it on your computer to check it and see the lyrics on screen with the music.
14. Delete the submenu and repeat steps 7-13 for the next song. Phew!!!!
15. The tutorial mentioned above describes how to assemble videos with menus onto a DVD but I can tell you how if necessary. I discovered you are limited to 36 buttons per menu and 128 pre and post calls on the DVD which effectively means 40 songs max per DVD. Also I will explain multi verse songs with the verses changing as the music plays if you want that.
All the best and have much patience
Peter

---

### Post by nitep on 2009-04-09
To continue
First a correction to step 5 above, the size of your jpeg or png makes no difference so best to keep a high resolution. The resolution is sorted out at step 8 above. I had a misunderstanding about that.
To have the lyrics change on screen with a multi verse song I would have preferred to use QDVDAuthor's slideshow option but I cannot get it to work. Instead I did the following using the song "How Great Thou Art" as an example to show verse 1 lyrics as the verse is heard etc
There are 4 verses each followed by a chorus.
16. I used ReZound to split the audio into 8 pieces.
17. Open the mp3 file and start it playing. When you hear the first verse finish click at that point.
18. The lighter blue is then the selected part which is from the point you clicked to the end of the song.
19. Stop the music and click on Edit. Move the mouse to the bottom of the menu over Selection, then over to flip to beginning so that now just the first verse is selected.
    ie Edit-->Selection-->flip to beginning
20. Then got to File-->Save Selection As  and save it as v1.mp3
21. Now do Ctrl X  or Edit-->Cut to remove v1 form the sound track
22. Repeat 17 to 21 for the chorus saving it as c1.mp3 etc
23. You will end up with v1,c1,v2,c2,v3,c3,v4,c4.  You cannot get away with just one chorus or when you join it all together later there will be a blip in the audio. At step 2 above you are really only deciding when the lyrics will change so you dont have to be too accurate.
24. Repeat step 5 above to get 4 separate verses as jpeg or png and here you only need the chorus once.
25. Do steps 6 to 14 above to get a video clip of v1 and save it in a temp subfolder as 1.VOB
26. Do step 25 for c1 and save it as 2.VOB
27. Do step 25 for v2 and save it as 3.VOB
28. Do step 25 for c2 and save it as 4.VOB
29. Do step 25 for v3 and save it as 5.VOB 
30. Etc ending with the last chorus as 8.VOB  You can play one or more to test them.
31. Now to join the 8 video clips together. Start Avidemux
32. Open 1.VOB  It will say "do you want to index it"? You have to answer "yes"
33. It should say "There are several mpeg files, append them?" Answer "yes" It joins them in alphabetic order which is why we saved them as 1 to 8 or you can use File-->Append 
34. To save the finished product on the left hand side set Format to mpeg-PS(A+V)
35. and then set audio to MP2(two LAME)
36. Click on Save and give the file name as    How Great Thou Art.VOB
37. Now play it and you will see the verses changing on screen.

The software mentioned so far
Sound Converter, Avidemux, ReZound and QDVDAuthor is all available through Ubuntu's Applications-->Add/Remove

You have not let me know how you are getting on Chuck.

---

### Post by nitep on 2009-04-12
37. By now you have a video folder of many songs with meaningful names such as "How Great Thou Art.VOB", so we need to print a song list. Open a terminal and pipe the folder listing to a file i.e.
ls > song-list
Now open that file with a word processor and tidy it up by removing the .VOB from each song. I also numbered the songs for a DVD described below. You can then print a copy for each member of your group so they know what songs they can choose from.
38. If you have a laptop you can connect to your TV or a data projector then the job is finished as you can easily choose and play any song. You can do that at church when all the musicians are away. For those who are less hi_tech such as me we need to make a DVD now.

39. Start QDVDAuthor and go to File-->New Project etc
40. Click on Add Background to get a pretty background
41. We now need a menu, so Right click on the background and left click on "add text"
42. Move the cross roughly to the required position and click. In the new window choose a font such as Impact and size such as 22
43. Click in the smaller text window and type 1-16 (for songs 1-16) then click on OK
44. This has to be defined as a button but cant be until you have stretched it by clicking in the correct place to produce an arrow to drag an edge.
45. Then right click and click "define as button". You can still move the button to where you want it.
46. Repeat steps 41-45 to produce a button 17-32 and then 33-40. We can only have 40 songs.
47. We need a sub menu so click on "DVDAuthor" at the top left 
and then click on "Add Menu".
48. In the sub menu window right click and then click on "Rename Menu". 
Give the name 1-16. Then do step 40 above
49. Click on the "main Menu VMGM" tab then right click and click on "Edit Button"
50. I have not tried this but under action it might be best to select call. I have always left it at jump but it is slightly messy getting back when the jump is finished. Anyway beside the mini Action window select 1-16. 
This connects the main menu button 1-16 to the sub menu called 1-16. You will see the structure in the bottom left window. It pays to save the project periodically in case of a crash, which does happen with DVDAuthor.
60. Repeat steps 47-50 to make and link the other buttons to sub menus.
61. Now we need to add movies which are the small VOB songs created earlier.
62. Right click in the white space of the top left window. (When you run out of white space you can drag the edge to make the window wider.) Browse to your VOB folder click on one song and click on open. It will appear at the top left in a light blue colour. (If it is a purple colour then you encoded it wrongly at step 34,35. In that case right click on the purple and delete it. Do  step 34,35 again correctly and repeat 62)
63. Repeat step 62 for each song one at a time. If you select several songs at once they will be played together so that you cannot select one from the finished DVD. Remember to save the project periodically in case of a crash.
64. We now need a button for each song and we need to link it to the required song.
65. Go to sub menu 1-16 and add a background.
66. Do step 41-45 to create a button "1", then right click and click on "Edit Button".
67. Beside the mini Action window select the correct song that the button will jump to (or perhaps better call to) You will have to look at your printed song list to see which is song number 1.
68. Create up to 39 more buttons in the appropriate sub menus and link to the appropriate songs saving the project often.
69. Now click on "Create DVD". When it is finished the DVD contents are the entire contents of the VIDEO_TS folder that is produced.
70. You can now you can burn it to DVD with the terminal command

growisofs -Z /dev/dvd -dvd-video /home/peter/temp

where in my case  /home/peter/temp is the folder containing the VIDEO_TS folder

71. Test your DVD in your DVD player. When a song is finished I had to press >>| 
(that is the next button) on the DVD player remote control to get to the sub menu. Pushing next button again got me to the TRANSONIC DVD screen but pushing the MENU button then got me to the DVD main menu with the 1-16 etc buttons. Testing it on another DVD player required pushing a TOP MENU button button. You will have to try it but it has worked in 3 different DVD players so far with no failures except when I did not wait for a song to finish, then pushing buttons on the remote crashed the DVD player so the I had to disconnect the power to regain control.

---

