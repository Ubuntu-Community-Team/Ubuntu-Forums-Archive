---
title: "Could someone help me with a bash script please."
date: 2009-08-02
forum: The Cafe
---

### Post by swoll1980 on 2009-08-02
I need a bash script that will replace all of the spaces in my file names with underscores. Is such a thing possible?

---

### Post by cariboo on 2009-08-02
Try:

```
for i in *.mp3; do mv "$i" `echo $i | tr ' ' '_'`; done 
```

Change the mp3 to the extension of your files.

The script is from this [howto]("http:///tldp.org/HOWTO/MP3-CD-Burning/audio.html#PREPARE").

---

### Post by sisco311 on 2009-08-02
try something like:
```
find /path/to/dir -type f -name "* *" | while read file; do **echo** mv -b "$file" "${file// /_}"; done
```

remove the **echo** command to actually rename the files.

NOTE: find will search for files recursively.

---

### Post by arsenic23 on 2009-08-02
If its just in one directory you could just use the rename command.

```
rename 's/\ /_/g' *
```

---

### Post by swoll1980 on 2009-08-02
There's a directory "music" in it are about 100 subfolders I want to  rename all the file inside all of them. /home/nolan/music is the directory.

---

### Post by Mornedhel on 2009-08-02
> **arsenic23 said:**
> If its just in one directory you could just use the rename command.

```
rename 's/\ /_/g' *
```

Spaces are not metacharacters in Perl style regular expressions, you don't need to escape them. Actually, I don't think they are metacharacters in any kind of regular expressions.

Also, rename won't recurse into the subdirectories.

---

### Post by arsenic23 on 2009-08-02
> **Mornedhel said:**
> Spaces are not metacharacters in Perl style regular expressions, you don't need to escape them. Actually, I don't think they are metacharacters in any kind of regular expressions.

I had an installation of something weird back in 06 (when I was learning regex) that didn't like nonescaped spaces.  I do it out of habit; it doesn't hurt anything.

> **Mornedhel said:**
> Also, rename won't recurse into the subdirectories.

Yeah, that's what I said.

---

### Post by swoll1980 on 2009-08-02
> **sisco311 said:**
> try something like:
```
find /path/to/dir -type f -name "* *" | while read file; do **echo** mv -b "$file" "${file// /_}"; done
```

remove the **echo** command to actually rename the files.

NOTE: find will search for files recursively.

```
 `/home/nolan/music/80\'s/Air_Supply/Air_Supply_-_All_Out_Of_Love.mp3': No such file or directory
mv: cannot move `/home/nolan/music/80\'s/Air Supply/Love - Air Supply - Even The Nights Are Better.mp3' to `/home/nolan/music/80\'s/Air_Supply/Love_-_Air_Supply_-_Even_The_Nights_Are_Better.mp3': No such file or directory
mv: cannot move `/home/nolan/music/80\'s/Van Stevenson/Van Stephenson  - Modern Day Delilah .mp3' to `/home/nolan/music/80\'s/Van_Stevenson/Van_Stephenson__-_Modern_Day_Delilah_.mp3': No such file or directory
mv: cannot move `/home/nolan/music/80\'s/The Ramones/Ramones - I Wanna Be Sedated.mp3' to `/home/nolan/music/80\'s/The_Ramones/Ramones_-_I_Wanna_Be_Sedated.mp3': No such file or directory
mv: cannot move `/home/nolan/music/70\'s/John Denver/John Denver & Placido Domingo - Perhaps love.mp3' to `/home/nolan/music/70\'s/John_Denver/John_Denver_&_Placido_Domingo_-_Perhaps_love.mp3': No such file or directory
mv: cannot move `/home/nolan/music/70\'s/John Denver/John Denver - Like A Sad Song.mp3' to `/home/nolan/music/70\'s/John_Denver/John_Denver_-_Like_A_Sad_Song.mp3': No such file or directory
mv: cannot move `/home/nolan/music/70\'s/John Denver/John Denver - Leaving On A Jet Plane.mp3' to `/home/nolan/music/70\'s/John_Denver/John_Denver_-_Leaving_On_A_Jet_Plane.mp3': No such file or directory
mv: cannot move `/home/nolan/music/70\'s/John Denver/John Denver - Rocky Mountain High(1).mp3' to `/home/nolan/music/70\'s/John_Denver/John_Denver_-_Rocky_Mountain_High(1).mp3': No such file or directory
mv: cannot move `/home/nolan/music/70\'s/John Denver/John Denver - Hey it\'s good to be back home again.mp3' to `/home/nolan/music/70\'s/John_Denver/John_Denver_-_Hey_it\'s_good_to_be_back_home_again.mp3': No such file or directory
mv: cannot move `/home/nolan/music/70\'s/John Denver/John Denver - Annie\'s Song.mp3' to `/home/nolan/music/70\'s/John_Denver/John_Denver_-_Annie\'s_Song.mp3': No such file or directory
mv: cannot move `/home/nolan/music/70\'s/John Denver/Sunshine On My Shoulder.mp3' to `/home/nolan/music/70\'s/John_Denver/Sunshine_On_My_Shoulder.mp3': No such file or directory
mv: cannot move `/home/nolan/music/70\'s/John Denver/John Denver - Last Night I Had The Strangest Dream (RARE).mp3' to `/home/nolan/music/70\'s/John_Denver/John_Denver_-_Last_Night_I_Had_The_Strangest_Dream_(RARE).mp3': No such file or directory
mv: cannot move `/home/nolan/music/70\'s/John Denver/John Denver  This Old Guitar.mp3' to `/home/nolan/music/70\'s/John_Denver/John_Denver__This_Old_Guitar.mp3': No such file or directory
mv: cannot move `/home/nolan/music/70\'s/John Denver/John Denver - I\'m Sorry.mp3' to `/home/nolan/music/70\'s/John_Denver/John_Denver_-_I\'m_Sorry.mp3': No such file or directory
mv: cannot move `/home/nolan/music/70\'s/James Taylor/06 You\'ve Got A Friend.mp3' to `/home/nolan/music/70\'s/James_Taylor/06_You\'ve_Got_A_Friend.mp3': No such file or directory
mv: cannot move `/home/nolan/music/70\'s/James Taylor/James Taylor  - Shower the People You Love with Love.mp3' to `/home/nolan/music/70\'s/James_Taylor/James_Taylor__-_Shower_the_People_You_Love_with_Love.mp3': No such file or directory
mv: cannot move `/home/nolan/music/Girley Rock/The Cardigans/The Cardigans - Lovefool.mp3' to `/home/nolan/music/Girley_Rock/The_Cardigans/The_Cardigans_-_Lovefool.mp3': No such file or directory
mv: cannot move `/home/nolan/music/Girley Rock/Michelle Branch/Michelle Branch- Leave The Pieces.mp3' to `/home/nolan/music/Girley_Rock/Michelle_Branch/Michelle_Branch-_Leave_The_Pieces.mp3': No such file or directory
mv: cannot move `/home/nolan/music/Girley Rock/Anna Nalick/Anna Nalick-Just Breathe.mp3' to `/home/nolan/music/Girley_Rock/Anna_Nalick/Anna_Nalick-Just_Breathe.mp3': No such file or directory
mv: cannot move `/home/nolan/music/Classic Rock/Styx/love at first sight styx.mp3' to `/home/nolan/music/Classic_Rock/Styx/love_at_first_sight_styx.mp3': No such file or directory
mv: cannot move `/home/nolan/music/Classic Rock/Styx/80s- Styxx - Mr.Roboto.mp3' to `/home/nolan/music/Classic_Rock/Styx/80s-_Styxx_-_Mr.Roboto.mp3': No such file or directory
mv: cannot move `/home/nolan/music/Classic Rock/Bob Sieger/Bob Sieger - Night Moves.mp3' to `/home/nolan/music/Classic_Rock/Bob_Sieger/Bob_Sieger_-_Night_Moves.mp3': No such file or directory
mv: cannot move `/home/nolan/music/Classic Rock/Bob Sieger/Bob Sieger - We\'ve Got Tonight.mp3' to `/home/nolan/music/Classic_Rock/Bob_Sieger/Bob_Sieger_-_We\'ve_Got_Tonight.mp3': No such file or directory
mv: cannot move `/home/nolan/music/Classic Rock/Fleetwood Mack/Fleetwood mack- Land Slide.mp3' to `/home/nolan/music/Classic_Rock/Fleetwood_Mack/Fleetwood_mack-_Land_Slide.mp3': No such file or directory
mv: cannot move `/home/nolan/music/Classic Rock/Brian Adams/Bryan Adams - Best Days Of My Life.mp3' to `/home/nolan/music/Classic_Rock/Brian_Adams/Bryan_Adams_-_Best_Days_Of_My_Life.mp3': No such file or directory
mv: cannot move `/home/nolan/music/Classic Rock/Brian Adams/Brian Adams - I Can\'t Stop Loving You.mp3' to `/home/nolan/music/Classic_Rock/Brian_Adams/Brian_Adams_-_I_Can\'t_Stop_Loving_You.mp3': No such file or directory
mv: cannot move `/home/nolan/music/Classic Rock/Kansas/Lenard Skynard - Freebird.mp3' to `/home/nolan/music/Classic_Rock/Kansas/Lenard_Skynard_-_Freebird.mp3': No such file or directory
mv: cannot move `/home/nolan/music/Classic Rock/Dire Straits/Dire Straits - Straights - Sultans of Swing.mp3' to `/home/nolan/music/Classic_Rock/Dire_Straits/Dire_Straits_-_Straights_-_Sultans_of_Swing.mp3': No such file or directory
mv: cannot move `/home/nolan/music/Classic Rock/Rod Stewert/Rod Stewert - The First Cut Is The Deepest - .mp3' to `/home/nolan/music/Classic_Rock/Rod_Stewert/Rod_Stewert_-_The_First_Cut_Is_The_Deepest_-_.mp3': No such file or directory
mv: cannot move `/home/nolan/music/Classic Rock/Rod Stewert/Rod Stewart - Have I Told You Latley That I Love You.mp3' to `/home/nolan/music/Classic_Rock/Rod_Stewert/Rod_Stewart_-_Have_I_Told_You_Latley_That_I_Love_You.mp3': No such file or directory
mv: cannot move `/home/nolan/music/Classic Rock/Rod Stewert/Rod Stewart - Wake Up Maggie .mp3' to `/home/nolan/music/Classic_Rock/Rod_Stewert/Rod_Stewart_-_Wake_Up_Maggie_.mp3': No such file or directory
mv: cannot move `/home/nolan/music/Classic Rock/Aerosmith/Aerosmith - What It Takes.mp3' to `/home/nolan/music/Classic_Rock/Aerosmith/Aerosmith_-_What_It_Takes.mp3': No such file or directory
mv: cannot move `/home/nolan/music/Classic Rock/Aerosmith/Aerosmith - Janie\'s Got A Gun.mp3' to `/home/nolan/music/Classic_Rock/Aerosmith/Aerosmith_-_Janie\'s_Got_A_Gun.mp3': No such file or directory
mv: cannot move `/home/nolan/music/Classic Rock/Aerosmith/Aerosmith - I Don\'t Want To Miss A Thing.mp3' to `/home/nolan/music/Classic_Rock/Aerosmith/Aerosmith_-_I_Don\'t_Want_To_Miss_A_Thing.mp3': No such file or directory
mv: cannot move `/home/nolan/music/Classic Rock/Aerosmith/Aerosmith - Dream On.mp3' to `/home/nolan/music/Classic_Rock/Aerosmith/Aerosmith_-_Dream_On.mp3': No such file or directory
mv: cannot move `/home/nolan/music/Classic Rock/Aerosmith/Aerosmith - Crazy.mp3' to `/home/nolan/music/Classic_Rock/Aerosmith/Aerosmith_-_Crazy.mp3': No such file or directory
mv: cannot move `/home/nolan/music/Classic Rock/Aerosmith/Aerosmith - Living On The Edge.mp3' to `/home/nolan/music/Classic_Rock/Aerosmith/Aerosmith_-_Living_On_The_Edge.mp3': No such file or directory
mv: cannot move `/home/nolan/music/Classic Rock/Aerosmith/Aerosmith - Amazing.mp3' to `/home/nolan/music/Classic_Rock/Aerosmith/Aerosmith_-_Amazing.mp3': No such file or directory
mv: cannot move `/home/nolan/music/Classic Rock/Queensryche/Queensryche - Silent Lucidity.mp3' to `/home/nolan/music/Classic_Rock/Queensryche/Queensryche_-_Silent_Lucidity.mp3': No such file or directory
mv: cannot move `/home/nolan/music/Classic Rock/Elton John/Elton John - I Guess That\'s Why They Call It The Blues.mp3' to `/home/nolan/music/Classic_Rock/Elton_John/Elton_John_-_I_Guess_That\'s_Why_They_Call_It_The_Blues.mp3': No such file or directory
mv: cannot move `/home/nolan/music/Classic Rock/Elton John/Elton John - Can You Feel the Love Tonight - Walt Disney Pictures - The Lion King Soundtrack.mp3' to `/home/nolan/music/Classic_Rock/Elton_John/Elton_John_-_Can_You_Feel_the_Love_Tonight_-_Walt_Disney_Pictures_-_The_Lion_King_Soundtrack.mp3': No such file or directory
mv: cannot move `/home/nolan/music/Classic Rock/Elton John/Elton John - Benny and the Jets.mp3' to `/home/nolan/music/Classic_Rock/Elton_John/Elton_John_-_Benny_and_the_Jets.mp3': No such file or directory
mv: cannot move `/home/nolan/music/Classic Rock/Elton John/Elton John - Sad Songs Say So Much.mp3' to `/home/nolan/music/Classic_Rock/Elton_John/Elton_John_-_Sad_Songs_Say_So_Much.mp3': No such file or directory
mv: cannot move `/home/nolan/music/Classic Rock/Elton John/11 Goodbye Yellow Brick Road.m4a' to `/home/nolan/music/Classic_Rock/Elton_John/11_Goodbye_Yellow_Brick_Road.m4a': No such file or directory
mv: cannot move `/home/nolan/music/Classic Rock/Elton John/Elton John - Don\'t Let the Sun Go Down On Me.mp3' to `/home/nolan/music/Classic_Rock/Elton_John/Elton_John_-_Don\'t_Let_the_Sun_Go_Down_On_Me.mp3': No such file or directory
mv: cannot move `/home/nolan/music/Classic Rock/Elton John/Elton John - Mona Lisas and Madhatters.mp3' to `/home/nolan/music/Classic_Rock/Elton_John/Elton_John_-_Mona_Lisas_and_Madhatters.mp3': No such file or directory
mv: cannot move `/home/nolan/music/Classic Rock/Elton John/Elton John - Crocodile Rock.mp3' to `/home/nolan/music/Classic_Rock/Elton_John/Elton_John_-_Crocodile_Rock.mp3': No such file or directory
mv: cannot move `/home/nolan/music/Classic Rock/Elton John/Elton John - Someone Saved My Life Tonight.mp3' to `/home/nolan/music/Classic_Rock/Elton_John/Elton_John_-_Someone_Saved_My_Life_Tonight.mp3': No such file or directory
mv: cannot move `/home/nolan/music/Classic Rock/Elton John/Elton John - Candle in the Wind (Original).mp3' to `/home/nolan/music/Classic_Rock/Elton_John/Elton_John_-_Candle_in_the_Wind_(Original).mp3': No such file or directory
mv: cannot move `/home/nolan/music/Classic Rock/Journey/Journey-Steve Perry - Oh sherry.mp3' to `/home/nolan/music/Classic_Rock/Journey/Journey-Steve_Perry_-_Oh_sherry.mp3': No such file or directory
mv: cannot move `/home/nolan/music/Classic Rock/Journey/Journey - Oh Sherry.mp3' to `/home/nolan/music/Classic_Rock/Journey/Journey_-_Oh_Sherry.mp3': No such file or directory
mv: cannot move `/home/nolan/music/Classic Rock/Journey/Journey - Faithfully.mp3' to `/home/nolan/music/Classic_Rock/Journey/Journey_-_Faithfully.mp3': No such file or directory
mv: cannot move `/home/nolan/music/Classic Rock/Journey/Journey - Any Way You Want It.mp3' to `/home/nolan/music/Classic_Rock/Journey/Journey_-_Any_Way_You_Want_It.mp3': No such file or directory
mv: cannot move `/home/nolan/music/Classic Rock/Journey/Journey - Open Arms.mp3' to `/home/nolan/music/Classic_Rock/Journey/Journey_-_Open_Arms.mp3': No such file or directory
mv: cannot move `/home/nolan/music/Classic Rock/Journey/Journey - When The Lights Go Down In The City.mp3' to `/home/nolan/music/Classic_Rock/Journey/Journey_-_When_The_Lights_Go_Down_In_The_City.mp3': No such file or directory
mv: cannot move `/home/nolan/music/Classic Rock/Journey/Journey - Only The Young.mp3' to `/home/nolan/music/Classic_Rock/Journey/Journey_-_Only_The_Young.mp3': No such file or directory
mv: cannot move `/home/nolan/music/Classic Rock/Journey/Journey- When You Love a Woman.mp3' to `/home/nolan/music/Classic_Rock/Journey/Journey-_When_You_Love_a_Woman.mp3': No such file or directory
mv: cannot move `/home/nolan/music/Classic Rock/Journey/Journey - Wheel In The Sky.mp3' to `/home/nolan/music/Classic_Rock/Journey/Journey_-_Wheel_In_The_Sky.mp3': No such file or directory
mv: cannot move `/home/nolan/music/Classic Rock/Journey/Journey - Loving, Touching, Squeezing.mp3' to `/home/nolan/music/Classic_Rock/Journey/Journey_-_Loving,_Touching,_Squeezing.mp3': No such file or directory
mv: cannot move `/home/nolan/music/Classic Rock/Journey/Journey - Foolish Hearts.mp3' to `/home/nolan/music/Classic_Rock/Journey/Journey_-_Foolish_Hearts.mp3': No such file or directory
mv: cannot move `/home/nolan/music/Classic Rock/Ozzie/ozzie osborne - ozzy osbourne - shot in the dark.mp3' to `/home/nolan/music/Classic_Rock/Ozzie/ozzie_osborne_-_ozzy_osbourne_-_shot_in_the_dark.mp3': No such file or directory
mv: cannot move `/home/nolan/music/Classic Rock/Ozzie/Ozzie Osborne - No More Tears.mp3' to `/home/nolan/music/Classic_Rock/Ozzie/Ozzie_Osborne_-_No_More_Tears.mp3': No such file or directory
mv: cannot move `/home/nolan/music/Classic Rock/Black Sabith/Black Sabbath - Crazy Train.mp3' to `/home/nolan/music/Classic_Rock/Black_Sabith/Black_Sabbath_-_Crazy_Train.mp3': No such file or directory
mv: cannot move `/home/nolan/music/Classic Rock/Kiss/KISS - School\'s Out for the Summer.MP3' to `/home/nolan/music/Classic_Rock/Kiss/KISS_-_School\'s_Out_for_the_Summer.MP3': No such file or directory
mv: cannot move `/home/nolan/music/Classic Rock/Lenard Skynard/Lenard Skynard - Sweet Home Alabama.mp3' to `/home/nolan/music/Classic_Rock/Lenard_Skynard/Lenard_Skynard_-_Sweet_Home_Alabama.mp3': No such file or directory
mv: cannot move `/home/nolan/music/Classic Rock/Lenard Skynard/Lenard Skynard - That Smell.mp3' to `/home/nolan/music/Classic_Rock/Lenard_Skynard/Lenard_Skynard_-_That_Smell.mp3': No such file or directory
mv: cannot move `/home/nolan/music/Classic Rock/Lenard Skynard/Lenard Skynard - Tuesdays Gone.mp3' to `/home/nolan/music/Classic_Rock/Lenard_Skynard/Lenard_Skynard_-_Tuesdays_Gone.mp3': No such file or directory
mv: cannot move `/home/nolan/music/Classic Rock/Blue Oyster Cult/Blue Oyster Cult - Dont Fear The Reaper.mp3' to `/home/nolan/music/Classic_Rock/Blue_Oyster_Cult/Blue_Oyster_Cult_-_Dont_Fear_The_Reaper.mp3': No such file or directory
mv: cannot move `/home/nolan/music/Classic Rock/Led Zeplin/Led Zeplin- Stairway To Heaven.mp3' to `/home/nolan/music/Classic_Rock/Led_Zeplin/Led_Zeplin-_Stairway_To_Heaven.mp3': No such file or directory
mv: cannot move `/home/nolan/music/Classic Rock/Marshall Tucker Band/Marshall Tucker Band - Can\'t You See.mp3' to `/home/nolan/music/Classic_Rock/Marshall_Tucker_Band/Marshall_Tucker_Band_-_Can\'t_You_See.mp3': No such file or directory
mv: cannot move `/home/nolan/music/Classic Rock/Cat Stevens/Cat Stevens - Father and Son.mp3' to `/home/nolan/music/Classic_Rock/Cat_Stevens/Cat_Stevens_-_Father_and_Son.mp3': No such file or directory
mv: cannot move `/home/nolan/music/Classic Rock/Bad Company/bad company - All Right Now.mp3' to `/home/nolan/music/Classic_Rock/Bad_Company/bad_company_-_All_Right_Now.mp3': No such file or directory
mv: cannot move `/home/nolan/music/Classic Rock/Bad Company/Bad Company - Rock \'n\' Roll Fantasy.mp3' to `/home/nolan/music/Classic_Rock/Bad_Company/Bad_Company_-_Rock_\'n\'_Roll_Fantasy.mp3': No such file or directory
mv: cannot move `/home/nolan/music/Classic Rock/Bad Company/Bad Company - Bad Company.mp3' to `/home/nolan/music/Classic_Rock/Bad_Company/Bad_Company_-_Bad_Company.mp3': No such file or directory
mv: cannot move `/home/nolan/music/Classic Rock/Bad Company/Bad Company - Shooting Star (1).mp3' to `/home/nolan/music/Classic_Rock/Bad_Company/Bad_Company_-_Shooting_Star_(1).mp3': No such file or directory
mv: cannot move `/home/nolan/music/Classic Rock/Bad Company/Bad Company - Cant Get Enough of Your Love.mp3' to `/home/nolan/music/Classic_Rock/Bad_Company/Bad_Company_-_Cant_Get_Enough_of_Your_Love.mp3': No such file or directory
mv: cannot move `/home/nolan/music/Classic Rock/Bad Company/bad company - if you needed somebody.mp3' to `/home/nolan/music/Classic_Rock/Bad_Company/bad_company_-_if_you_needed_somebody.mp3': No such file or directory
mv: cannot move `/home/nolan/music/Classic Rock/Bad Company/Bad Company - I Feel Like Making Love.mp3' to `/home/nolan/music/Classic_Rock/Bad_Company/Bad_Company_-_I_Feel_Like_Making_Love.mp3': No such file or directory
mv: cannot move `/home/nolan/music/Classic Rock/The Rolling Stones/The Rolling Stones - Satisfaction.mp3' to `/home/nolan/music/Classic_Rock/The_Rolling_Stones/The_Rolling_Stones_-_Satisfaction.mp3': No such file or directory
mv: cannot move `/home/nolan/music/Classic Rock/The Rolling Stones/rolling stones - time is on my side.mp3' to `/home/nolan/music/Classic_Rock/The_Rolling_Stones/rolling_stones_-_time_is_on_my_side.mp3': No such file or directory
mv: cannot move `/home/nolan/music/Classic Rock/The Rolling Stones/Rolling Stones - Angie.mp3' to `/home/nolan/music/Classic_Rock/The_Rolling_Stones/Rolling_Stones_-_Angie.mp3': No such file or directory
mv: cannot move `/home/nolan/music/Classic Rock/The Rolling Stones/The Rolling Stones - Paint It Black.mp3' to `/home/nolan/music/Classic_Rock/The_Rolling_Stones/The_Rolling_Stones_-_Paint_It_Black.mp3': No such file or directory
mv: cannot move `/home/nolan/music/Classic Rock/The Rolling Stones/The Rolling Stones - Start Me Up.mp3' to `/home/nolan/music/Classic_Rock/The_Rolling_Stones/The_Rolling_Stones_-_Start_Me_Up.mp3': No such file or directory
mv: cannot move `/home/nolan/music/Classic Rock/Queen/Queen - We Will Rock You.mp3' to `/home/nolan/music/Classic_Rock/Queen/Queen_-_We_Will_Rock_You.mp3': No such file or directory
mv: cannot move `/home/nolan/music/Classic Rock/Queen/Queen - Killer Queen.mp3' to `/home/nolan/music/Classic_Rock/Queen/Queen_-_Killer_Queen.mp3': No such file or directory
mv: cannot move `/home/nolan/music/Classic Rock/Queen/Queen - I Want to Ride My Bicycle.mp3' to `/home/nolan/music/Classic_Rock/Queen/Queen_-_I_Want_to_Ride_My_Bicycle.mp3': No such file or directory
mv: cannot move `/home/nolan/music/Classic Rock/Queen/queen - you\'re my best friend.mp3' to `/home/nolan/music/Classic_Rock/Queen/queen_-_you\'re_my_best_friend.mp3': No such file or directory
mv: cannot move `/home/nolan/music/Classic Rock/Queen/Queen - Somebody To Love.mp3' to `/home/nolan/music/Classic_Rock/Queen/Queen_-_Somebody_To_Love.mp3': No such file or directory
mv: cannot move `/home/nolan/music/Classic Rock/Queen/Queen - Crazy little thing called love.mp3' to `/home/nolan/music/Classic_Rock/Queen/Queen_-_Crazy_little_thing_called_love.mp3': No such file or directory
mv: cannot move `/home/nolan/music/Classic Rock/Queen/Queen - Fat Bottomed Girls.mp3' to `/home/nolan/music/Classic_Rock/Queen/Queen_-_Fat_Bottomed_Girls.mp3': No such file or directory
mv: cannot move `/home/nolan/music/Classic Rock/Queen/Queen- Bohemian Raphsody.mp3' to `/home/nolan/music/Classic_Rock/Queen/Queen-_Bohemian_Raphsody.mp3': No such file or directory
mv: cannot move `/home/nolan/music/Classic Rock/Queen/David Bowie & Queen - Under Pressure.mp3' to `/home/nolan/music/Classic_Rock/Queen/David_Bowie_&_Queen_-_Under_Pressure.mp3': No such file or directory
mv: cannot move `/home/nolan/music/Classic Rock/Queen/Queen - Another One Bites The Dust.mp3' to `/home/nolan/music/Classic_Rock/Queen/Queen_-_Another_One_Bites_The_Dust.mp3': No such file or directory
mv: cannot move `/home/nolan/music/Classic Rock/Pink Floyd/Pink Floyd - Welcome to the Machine.mp3' to `/home/nolan/music/Classic_Rock/Pink_Floyd/Pink_Floyd_-_Welcome_to_the_Machine.mp3': No such file or directory
mv: cannot move `/home/nolan/music/Classic Rock/Pink Floyd/Pink Floyd - Wish You Were Here.mp3' to `/home/nolan/music/Classic_Rock/Pink_Floyd/Pink_Floyd_-_Wish_You_Were_Here.mp3': No such file or directory
mv: cannot move `/home/nolan/music/Classic Rock/Pink Floyd/Pink Floyd - The Fletcher Memorial Home.mp3' to `/home/nolan/music/Classic_Rock/Pink_Floyd/Pink_Floyd_-_The_Fletcher_Memorial_Home.mp3': No such file or directory
mv: cannot move `/home/nolan/music/Classic Rock/Pink Floyd/The Wall 2/Pink Floyd - The Show Must Go On.mp3' to `/home/nolan/music/Classic_Rock/Pink_Floyd/The_Wall_2/Pink_Floyd_-_The_Show_Must_Go_On.mp3': No such file or directory
mv: cannot move `/home/nolan/music/Classic Rock/Pink Floyd/The Wall 2/Pink Floyd - The Trial.mp3' to `/home/nolan/music/Classic_Rock/Pink_Floyd/The_Wall_2/Pink_Floyd_-_The_Trial.mp3': No such file or directory
mv: cannot move `/home/nolan/music/Classic Rock/Pink Floyd/The Wall 2/PinkFloyd - Is There Anybody Out There.mp3' to `/home/nolan/music/Classic_Rock/Pink_Floyd/The_Wall_2/PinkFloyd_-_Is_There_Anybody_Out_There.mp3': No such file or directory
mv: cannot move `/home/nolan/music/Classic Rock/Pink Floyd/The Wall 2/Pink Floyd - Nobody Home.mp3' to `/home/nolan/music/Classic_Rock/Pink_Floyd/The_Wall_2/Pink_Floyd_-_Nobody_Home.mp3': No such file or directory
mv: cannot move `/home/nolan/music/Classic Rock/Pink Floyd/The Wall 2/Pink Floyd - Run Like Hell.mp3' to `/home/nolan/music/Classic_Rock/Pink_Floyd/The_Wall_2/Pink_Floyd_-_Run_Like_Hell.mp3': No such file or directory
mv: cannot move `/home/nolan/music/Classic Rock/Pink Floyd/The Wall 2/10-Waiting for the Worms.mp3' to `/home/nolan/music/Classic_Rock/Pink_Floyd/The_Wall_2/10-Waiting_for_the_Worms.mp3': No such file or directory
mv: cannot move `/home/nolan/music/Classic Rock/Pink Floyd/The Wall 2/Pink Floyd - Comfortably Numb.mp3' to `/home/nolan/music/Classic_Rock/Pink_Floyd/The_Wall_2/Pink_Floyd_-_Comfortably_Numb.mp3': No such file or directory
mv: cannot move `/home/nolan/music/Classic Rock/Pink Floyd/The Wall 2/Pink Floyd - Hey You.mp3' to `/home/nolan/music/Classic_Rock/Pink_Floyd/The_Wall_2/Pink_Floyd_-_Hey_You.mp3': No such file or directory
mv: cannot move `/home/nolan/music/Classic Rock/Pink Floyd/The Wall 2/Pink Floyd - Bring The Boys Back Home.mp3' to `/home/nolan/music/Classic_Rock/Pink_Floyd/The_Wall_2/Pink_Floyd_-_Bring_The_Boys_Back_Home.mp3': No such file or directory
mv: cannot move `/home/nolan/music/Classic Rock/Pink Floyd/The Wall 2/Pink Floyd - 04 Vera.mp3' to `/home/nolan/music/Classic_Rock/Pink_Floyd/The_Wall_2/Pink_Floyd_-_04_Vera.mp3': No such file or directory
mv: cannot move `/home/nolan/music/Classic Rock/Pink Floyd/The Wall 2/13 - Pink Floyd - Outside T.mp3' to `/home/nolan/music/Classic_Rock/Pink_Floyd/The_Wall_2/13_-_Pink_Floyd_-_Outside_T.mp3': No such file or directory
mv: cannot move `/home/nolan/music/Classic Rock/Pink Floyd/The Wall 1/Pink Floyd - The Happiest Days of our Lives.mp3' to `/home/nolan/music/Classic_Rock/Pink_Floyd/The_Wall_1/Pink_Floyd_-_The_Happiest_Days_of_our_Lives.mp3': No such file or directory
mv: cannot move `/home/nolan/music/Classic Rock/Pink Floyd/The Wall 1/Roger Waters - Young Lust.mp3' to `/home/nolan/music/Classic_Rock/Pink_Floyd/The_Wall_1/Roger_Waters_-_Young_Lust.mp3': No such file or directory
mv: cannot move `/home/nolan/music/Classic Rock/Pink Floyd/The Wall 1/01 - In The Flesh.mp3' to `/home/nolan/music/Classic_Rock/Pink_Floyd/The_Wall_1/01_-_In_The_Flesh.mp3': No such file or directory
mv: cannot move `/home/nolan/music/Classic Rock/Pink Floyd/The Wall 1/Pink Floyd - 11. Dont Leave Me Now.mp3' to `/home/nolan/music/Classic_Rock/Pink_Floyd/The_Wall_1/Pink_Floyd_-_11._Dont_Leave_Me_Now.mp3': No such file or directory
mv: cannot move `/home/nolan/music/Classic Rock/Pink Floyd/The Wall 1/02 The Thin Ice.mp3' to `/home/nolan/music/Classic_Rock/Pink_Floyd/The_Wall_1/02_The_Thin_Ice.mp3': No such file or directory
mv: cannot move `/home/nolan/music/Classic Rock/Pink Floyd/The Wall 1/pink floyd - good bye blue sky(1).mp3' to `/home/nolan/music/Classic_Rock/Pink_Floyd/The_Wall_1/pink_floyd_-_good_bye_blue_sky(1).mp3': No such file or directory
mv: cannot move `/home/nolan/music/Classic Rock/Pink Floyd/The Wall 1/Pink Floyd - Goodbye Cruel World.mp3' to `/home/nolan/music/Classic_Rock/Pink_Floyd/The_Wall_1/Pink_Floyd_-_Goodbye_Cruel_World.mp3': No such file or directory
mv: cannot move `/home/nolan/music/Classic Rock/Pink Floyd/Pink Floyd - On The Turning Away.mp3' to `/home/nolan/music/Classic_Rock/Pink_Floyd/Pink_Floyd_-_On_The_Turning_Away.mp3': No such file or directory
mv: cannot move `/home/nolan/music/Classic Rock/Pink Floyd/Pink Floyd - Learning to Fly.mp3' to `/home/nolan/music/Classic_Rock/Pink_Floyd/Pink_Floyd_-_Learning_to_Fly.mp3': No such file or directory
mv: cannot move `/home/nolan/music/Classic Rock/Pink Floyd/Pink Floyd - Shine On You Crazy Diamond.mp3' to `/home/nolan/music/Classic_Rock/Pink_Floyd/Pink_Floyd_-_Shine_On_You_Crazy_Diamond.mp3': No such file or directory
mv: cannot move `/home/nolan/music/Classic Rock/Boston/13 - Smokin\'.mp3' to `/home/nolan/music/Classic_Rock/Boston/13_-_Smokin\'.mp3': No such file or directory
mv: cannot move `/home/nolan/music/Classic Rock/Boston/11 - Amanda.mp3' to `/home/nolan/music/Classic_Rock/Boston/11_-_Amanda.mp3': No such file or directory
mv: cannot move `/home/nolan/music/Classic Rock/Boston/14 - A Man I\'ll Never Be.mp3' to `/home/nolan/music/Classic_Rock/Boston/14_-_A_Man_I\'ll_Never_Be.mp3': No such file or directory
mv: cannot move `/home/nolan/music/Classic Rock/Boston/03 - More Than A Feeling.mp3' to `/home/nolan/music/Classic_Rock/Boston/03_-_More_Than_A_Feeling.mp3': No such file or directory
mv: cannot move `/home/nolan/music/Classic Rock/Boston/08 - Feelin\' Satisfied.mp3' to `/home/nolan/music/Classic_Rock/Boston/08_-_Feelin\'_Satisfied.mp3': No such file or directory
mv: cannot move `/home/nolan/music/Classic Rock/Boston/01 - Tell Me.mp3' to `/home/nolan/music/Classic_Rock/Boston/01_-_Tell_Me.mp3': No such file or directory
mv: cannot move `/home/nolan/music/Classic Rock/Jim Croce/Jim Croce - Had To Say I Love You In A Song.mp3' to `/home/nolan/music/Classic_Rock/Jim_Croce/Jim_Croce_-_Had_To_Say_I_Love_You_In_A_Song.mp3': No such file or directory
mv: cannot move `/home/nolan/music/Classic Rock/Animals/Animals - House Of The Rising Sun (Hey this is not by Cream, The Rolling Stones, CCR, Led Zeppeli.mp3' to `/home/nolan/music/Classic_Rock/Animals/Animals_-_House_Of_The_Rising_Sun_(Hey_this_is_not_by_Cream,_The_Rolling_Stones,_CCR,_Led_Zeppeli.mp3': No such file or directory
mv: cannot move `/home/nolan/music/Classic Rock/Meat loaf/Meatloaf -  I\'d Do Anything For love (But I Won\'t Do That).mp3' to `/home/nolan/music/Classic_Rock/Meat_loaf/Meatloaf_-__I\'d_Do_Anything_For_love_(But_I_Won\'t_Do_That).mp3': No such file or directory
mv: cannot move `/home/nolan/music/Classic Rock/Meat loaf/Meatloaf - Life Is A Lemon And I Want My Money Back.mp3' to `/home/nolan/music/Classic_Rock/Meat_loaf/Meatloaf_-_Life_Is_A_Lemon_And_I_Want_My_Money_Back.mp3': No such file or directory
mv: cannot move `/home/nolan/music/Classic Rock/Meat loaf/Meat Loaf - Paradise By The Dashboard Light.mp3' to `/home/nolan/music/Classic_Rock/Meat_loaf/Meat_Loaf_-_Paradise_By_The_Dashboard_Light.mp3': No such file or directory
mv: cannot move `/home/nolan/music/Classic Rock/Meat loaf/Meatloaf - Two Of Out Three Aint Bad.mp3' to `/home/nolan/music/Classic_Rock/Meat_loaf/Meatloaf_-_Two_Of_Out_Three_Aint_Bad.mp3': No such file or directory
mv: cannot move `/home/nolan/music/Classic Rock/Meat loaf/Meatloaf - You Took The Words Right Out Of My Mouth (1978) 1.mp3' to `/home/nolan/music/Classic_Rock/Meat_loaf/Meatloaf_-_You_Took_The_Words_Right_Out_Of_My_Mouth_(1978)_1.mp3': No such file or directory
mv: cannot move `/home/nolan/music/Soft Rock/Savage Garden/Savage Garden - Truely, Madly, Deeply.mp3' to `/home/nolan/music/Soft_Rock/Savage_Garden/Savage_Garden_-_Truely,_Madly,_Deeply.mp3': No such file or directory
mv: cannot move `/home/nolan/music/Soft Rock/Michael Bolton/Michael Bolton - When A Man Loves A Woman.mp3' to `/home/nolan/music/Soft_Rock/Michael_Bolton/Michael_Bolton_-_When_A_Man_Loves_A_Woman.mp3': No such file or directory
mv: cannot move `/home/nolan/music/Soft Rock/Chicago/Chicago - Youre the Inspiration.mp3' to `/home/nolan/music/Soft_Rock/Chicago/Chicago_-_Youre_the_Inspiration.mp3': No such file or directory
mv: cannot move `/home/nolan/music/Soft Rock/Chicago/Chicago  Stay The Night.mp3' to `/home/nolan/music/Soft_Rock/Chicago/Chicago__Stay_The_Night.mp3': No such file or directory
mv: cannot move `/home/nolan/music/Soft Rock/Chicago/Chicago - Glory of Love.mp3' to `/home/nolan/music/Soft_Rock/Chicago/Chicago_-_Glory_of_Love.mp3': No such file or directory
mv: cannot move `/home/nolan/music/Soft Rock/Chicago/Chicago - Hard Habit To Break.mp3' to `/home/nolan/music/Soft_Rock/Chicago/Chicago_-_Hard_Habit_To_Break.mp3': No such file or directory
mv: cannot move `/home/nolan/music/Soft Rock/Chicago/Chicago - If You Leave Me Now.mp3' to `/home/nolan/music/Soft_Rock/Chicago/Chicago_-_If_You_Leave_Me_Now.mp3': No such file or directory
mv: cannot move `/home/nolan/music/Soft Rock/Chicago/Chicago - Peter Cetera - Fight For Your Honor(Karate Kid).mp3' to `/home/nolan/music/Soft_Rock/Chicago/Chicago_-_Peter_Cetera_-_Fight_For_Your_Honor(Karate_Kid).mp3': No such file or directory
mv: cannot move `/home/nolan/music/Soft Rock/Chicago/Chicago - I Can\'t Fight This Feeling.mp3' to `/home/nolan/music/Soft_Rock/Chicago/Chicago_-_I_Can\'t_Fight_This_Feeling.mp3': No such file or directory
mv: cannot move `/home/nolan/music/Soft Rock/Don Henley/The Eagles - Desperado.mp3' to `/home/nolan/music/Soft_Rock/Don_Henley/The_Eagles_-_Desperado.mp3': No such file or directory
mv: cannot move `/home/nolan/music/Soft Rock/Don Henley/04 Patty & Don Henley - Sometimes when We Touch.mp3' to `/home/nolan/music/Soft_Rock/Don_Henley/04_Patty_&_Don_Henley_-_Sometimes_when_We_Touch.mp3': No such file or directory
mv: cannot move `/home/nolan/music/Soft Rock/Don Henley/The Eagles-Hotel California.mp3' to `/home/nolan/music/Soft_Rock/Don_Henley/The_Eagles-Hotel_California.mp3': No such file or directory
mv: cannot move `/home/nolan/music/Soft Rock/Don Henley/Don Henley & The Eagles - Heart Of The Matter (Forgiveness)(Live).mp3' to `/home/nolan/music/Soft_Rock/Don_Henley/Don_Henley_&_The_Eagles_-_Heart_Of_The_Matter_(Forgiveness)(Live).mp3': No such file or directory
mv: cannot move `/home/nolan/music/Soft Rock/Don Henley/Eagles - Take It Easy.mp3' to `/home/nolan/music/Soft_Rock/Don_Henley/Eagles_-_Take_It_Easy.mp3': No such file or directory
mv: cannot move `/home/nolan/music/Soft Rock/Don Henley/Eagles - The Last Worthless Evening - Don Henley.mp3' to `/home/nolan/music/Soft_Rock/Don_Henley/Eagles_-_The_Last_Worthless_Evening_-_Don_Henley.mp3': No such file or directory
mv: cannot move `/home/nolan/music/Soft Rock/Jewell/Jewell- You Were Meant For Me.mp3' to `/home/nolan/music/Soft_Rock/Jewell/Jewell-_You_Were_Meant_For_Me.mp3': No such file or directory
mv: cannot move `/home/nolan/music/Soft Rock/Jewell/Jewel - Foolish Games.mp3' to `/home/nolan/music/Soft_Rock/Jewell/Jewel_-_Foolish_Games.mp3': No such file or directory
mv: cannot move `/home/nolan/music/Soft Rock/Benny Mardones/Benny Mardones - If I Could Fly Into The Night.mp3' to `/home/nolan/music/Soft_Rock/Benny_Mardones/Benny_Mardones_-_If_I_Could_Fly_Into_The_Night.mp3': No such file or directory
mv: cannot move `/home/nolan/music/Hip Hop/Donell Jones/Donell Jones feat. Left Eye - U Know What\'s Up.mp3' to `/home/nolan/music/Hip_Hop/Donell_Jones/Donell_Jones_feat._Left_Eye_-_U_Know_What\'s_Up.mp3': No such file or directory
mv: cannot move `/home/nolan/music/Hip Hop/Color Me Bad/Color Me Badd - I Wanna Sex You Up.mp3' to `/home/nolan/music/Hip_Hop/Color_Me_Bad/Color_Me_Badd_-_I_Wanna_Sex_You_Up.mp3': No such file or directory
mv: cannot move `/home/nolan/music/Hip Hop/Pretty Ricky/Pretty Ricky - On The Hotline (DIRTY).mp3' to `/home/nolan/music/Hip_Hop/Pretty_Ricky/Pretty_Ricky_-_On_The_Hotline_(DIRTY).mp3': No such file or directory
mv: cannot move `/home/nolan/music/Hip Hop/Omarion/Omarion - Ice Box.mp3' to `/home/nolan/music/Hip_Hop/Omarion/Omarion_-_Ice_Box.mp3': No such file or directory
mv: cannot move `/home/nolan/music/Hip Hop/Britney Spears/Britney Spears - Gimme More.mp3' to `/home/nolan/music/Hip_Hop/Britney_Spears/Britney_Spears_-_Gimme_More.mp3': No such file or directory
mv: cannot move `/home/nolan/music/Hip Hop/Akon/Akon - Mr.Lonely.mp3' to `/home/nolan/music/Hip_Hop/Akon/Akon_-_Mr.Lonely.mp3': No such file or directory
mv: cannot move `/home/nolan/music/Hip Hop/Chris Brown/Chris Brown - Run It.mp3' to `/home/nolan/music/Hip_Hop/Chris_Brown/Chris_Brown_-_Run_It.mp3': No such file or directory
mv: cannot move `/home/nolan/music/Hip Hop/Chris Brown/Chris Brown - Gimmie That (Remix) (Feat Lil\' Wayne).mp3' to `/home/nolan/music/Hip_Hop/Chris_Brown/Chris_Brown_-_Gimmie_That_(Remix)_(Feat_Lil\'_Wayne).mp3': No such file or directory
mv: cannot move `/home/nolan/music/Hip Hop/112/112 - Peaches \'N Cream.mp3' to `/home/nolan/music/Hip_Hop/112/112_-_Peaches_\'N_Cream.mp3': No such file or directory
mv: cannot move `/home/nolan/music/Hip Hop/112/112 ft. Notorious BIG & Mase - Only You.mp3' to `/home/nolan/music/Hip_Hop/112/112_ft._Notorious_BIG_&_Mase_-_Only_You.mp3': No such file or directory
mv: cannot move `/home/nolan/music/Hip Hop/Allice Deejay/Alice Deejay - Better Off Alone (Dj Mystik & Dj Epic).mp3' to `/home/nolan/music/Hip_Hop/Allice_Deejay/Alice_Deejay_-_Better_Off_Alone_(Dj_Mystik_&_Dj_Epic).mp3': No such file or directory
mv: cannot move `/home/nolan/music/Hip Hop/Bobby Brown/Bobby Brown-Dont Be Cruel.mp3' to `/home/nolan/music/Hip_Hop/Bobby_Brown/Bobby_Brown-Dont_Be_Cruel.mp3': No such file or directory
mv: cannot move `/home/nolan/music/Hip Hop/Salt-N-Pepper/Salt-N-Pepper - None of your Business.mp3' to `/home/nolan/music/Hip_Hop/Salt-N-Pepper/Salt-N-Pepper_-_None_of_your_Business.mp3': No such file or directory
mv: cannot move `/home/nolan/music/Hip Hop/Ciara/Ciara - Like A Boy.mp3' to `/home/nolan/music/Hip_Hop/Ciara/Ciara_-_Like_A_Boy.mp3': No such file or directory
mv: cannot move `/home/nolan/music/Hip Hop/Ciara/Ciara feat. Ludacris - Oh.mp3' to `/home/nolan/music/Hip_Hop/Ciara/Ciara_feat._Ludacris_-_Oh.mp3': No such file or directory
mv: cannot move `/home/nolan/music/Hip Hop/T Pain/T-Pain Feat. Young Joc - Buy U A Drank.mp3' to `/home/nolan/music/Hip_Hop/T_Pain/T-Pain_Feat._Young_Joc_-_Buy_U_A_Drank.mp3': No such file or directory
mv: cannot move `/home/nolan/music/Hip Hop/T Pain/Smitty ft. T-Pain - Died in your arms tonight (Remix).mp3' to `/home/nolan/music/Hip_Hop/T_Pain/Smitty_ft._T-Pain_-_Died_in_your_arms_tonight_(Remix).mp3': No such file or directory
mv: cannot move `/home/nolan/music/Hip Hop/Nelly Furtado/Nelly Furtado - Say It Right.mp3' to `/home/nolan/music/Hip_Hop/Nelly_Furtado/Nelly_Furtado_-_Say_It_Right.mp3': No such file or directory
mv: cannot move `/home/nolan/music/Hip Hop/Christina Aguilera/Stripped/11 Beautiful.wma' to `/home/nolan/music/Hip_Hop/Christina_Aguilera/Stripped/11_Beautiful.wma': No such file or directory
```
nolan@Bigman:~$

---

### Post by swoll1980 on 2009-08-02
> **cariboo907 said:**
> Try:

```
for i in *.mp3; do mv "$i" `echo $i | tr ' ' '_'`; done 
```

Change the mp3 to the extension of your files.

The script is from this [howto]("http:///tldp.org/HOWTO/MP3-CD-Burning/audio.html#PREPARE").

```
mv: cannot stat `*.mp3': No such file or directory

```

---

### Post by koenn on 2009-08-02
> **swoll1980 said:**
> ```
mv: cannot stat `*.mp3': No such file or directory

```

are you running this from a directory that actually has .mp3 files in it ?

seems to work here
```


k@nix:~$ touch "aaa bbb ccc.mp3"
k@nix:~$ ls *.mp3
aaa bbb ccc.mp3

k@nix:~$ for i in *.mp3; do mv "$i" `echo $i | tr ' ' '_'`; done
k@nix:~$ ls *.mp3
aaa_bbb_ccc.mp3

```

---

### Post by swoll1980 on 2009-08-02
> **koenn said:**
> are you running this from a directory that actually has .mp3 files in it ?


No. If it's not recursive though, it won't be of much use. I would have to run it in a hundreds of different directories. 

The tree works like this.

Music > Genre > Artist > Album. So altogether there's way to many sub-directories in the music directory to run the command in. Thanks for the help though.

---

### Post by koenn on 2009-08-02
```
mv: cannot move
 `/home/nolan/music/Classic Rock/Bad Company/Bad Company - I Feel Like Making Love.mp3' 

to 

`/home/nolan/music/Classic_Rock/Bad_Company/Bad_Company_-_I_Feel_Like_Making_Love.mp3': No such file or directory
```

You're going to have to do this in stages.
Do you want all directories renamed as well, or just the files ?

---

### Post by swoll1980 on 2009-08-02
> **koenn said:**
> ```
mv: cannot move
 `/home/nolan/music/Classic Rock/Bad Company/Bad Company - I Feel Like Making Love.mp3' 

to 

`/home/nolan/music/Classic_Rock/Bad_Company/Bad_Company_-_I_Feel_Like_Making_Love.mp3': No such file or directory
```

You're going to have to do this in stages.
Do you want all directories renamed as well, or just the files ?

yeah, but just the files would be good enough.

---

### Post by JillSwift on 2009-08-02
```
find ./ -depth -name "*.mp3" -execdir rename 's/ /_/g' {} +
```

---

### Post by sisco311 on 2009-08-02
> **swoll1980 said:**
> ```
/home/nolan/music/80\'s/Air_Supply/Air_Supply_-_All_Out_Of_Love.mp3': No such file or directory
```
nolan@Bigman:~$
d'oh! 


this should work:
```
find /path/to/dir -type f -name "* *" | while read file; do echo mv -b "$file" "$(dirname "${file}")/$(basename "${file// /_}")"; done
```

---

### Post by koenn on 2009-08-02
or this
```

find ./ -type f -name "*.mp3" | while read file; do
     oldname=$(basename "$file"); 
     newname=$(echo $oldname | tr ' ' '_' ); 
     echo mv  "$file" "$(dirname "$file")/$newname"; 
done

```

---

### Post by koenn on 2009-08-02
> **JillSwift said:**
> ```
find ./ -depth -name "*.mp3" -execdir rename 's/ /_/g' {} +
```

this renames the directories ? 
does it work ?

---

### Post by JillSwift on 2009-08-02
> **koenn said:**
> this renames the directories ? No.
> **koenn said:**
> does it work ?Yes.

---

### Post by swoll1980 on 2009-08-02
Thanks guys. I will try this later. I'm logged into Windows right now.

---

### Post by sisco311 on 2009-08-02
> **koenn said:**
> this renames the directories ? 


only the *.mp3 directories :)

---

### Post by JillSwift on 2009-08-02
And on that, to rename both files and directories to replace spaces with underscores:

```
find ./ -depth -execdir rename 's/ /_/g' {} +
```

I've not factored in symlinks or anything of the like. It works dandy on just plain files and dirs. :)

---

### Post by koenn on 2009-08-02
> **JillSwift said:**
> And on that, to rename both files and directories to replace spaces with underscores:

```
find ./ -depth -execdir rename 's/ /_/g' {} +
```


ok, I think I get it (man find; man rename)  :)

---

### Post by sisco311 on 2009-08-03
here is the final(?) version (renames both files and directories):
```
find ./ -depth -name "* *" | while read file; do mv -b "$file" "$(dirname "${file}")/$(basename "${file// /_}")"; done
```


> **JillSwift said:**
> It works dandy on just plain files and dirs. :)

it works, but it's slow :)


for 1000 files with space in the filename + 200 files without space in name (+ 1 directory):
```

time find ./ -depth -execdir rename 's/ /_/g' {} +

real	0m49.587s
user	0m39.394s
sys	0m6.763s

----------------------------------------------------------------

time find ./ -depth -name "* *" -execdir rename 's/ /_/g' {} +

real	0m41.097s
user	0m33.035s
sys	0m5.850s

-------------------------------------------------------------------------------

time find ./ -depth -name "* *" | while read file; do mv -b "$file" "$(dirname "${file}")/$(basename "${file// /_}")"; done

real	0m13.576s
user	0m3.420s
sys	0m9.456s

```

---

### Post by toupeiro on 2009-08-03
Some of those find commands look good.  If you have too many files, you can always use xargs.  I like bash, but for some things, bash just isn't as efficient.  My default shell is tcsh, but to me, if you want to do this quick and easy (because depending on how many files you have, find can take some time), I recommend you give zsh a run...  I know you specifically asked for bash, and its far more popular, but if you're really unhappy with the performance and open to trying something different (and faster than piped find commands), then read on.

go to your location with all the files with spaces..


1) If you don't already have zsh on your system, type:> sudo apt-get install zsh zsh-doc, then type zsh to envoke the shell.

2) type:> autoload zmv

3) type: > zmv '(**/)(* *)' '$1${2// /_}'

If you really want to script it, put #!/bin/zsh at the top of an empty file, paste these lines, and make it executable.

This is a recursive command with the given syntax!

I would use zsh as my default shell but in truth it can really do much more than I need from a shell (I'd say in some aspects it compares to perl), so I just use it where and when I need to.  Always good to know a few tricks in another shell to save you some time, IMO.

---

### Post by thisllub on 2009-08-03
> **koenn said:**
> ```
mv: cannot move
 `/home/nolan/music/Classic Rock/Bad Company/Bad Company - I Feel Like Making Love.mp3' 

to 

`/home/nolan/music/Classic_Rock/Bad_Company/Bad_Company_-_I_Feel_Like_Making_Love.mp3': No such file or directory
```

You're going to have to do this in stages.
Do you want all directories renamed as well, or just the files ?

This is complaining about spaces.

You need to change the $IFS variable to something else.
Read this
[http://tldp.org/LDP/abs/html/internalvariables.html#IFSH](http://tldp.org/LDP/abs/html/internalvariables.html#IFSH)

---

### Post by koenn on 2009-08-03
> **thisllub said:**
> This is complaining about spaces.

it's not a solution, 
it illustrates the problem in previous solutions, namely that as the directory names get replaced, the mv command encounters non-existing paths in its destination parameter, and complains about it.

The solution is the -depth option to 'find', as seen in Jill's post, or using 'basename' to only convert filenames, not directories.

Read the thread.

---

### Post by sisco311 on 2009-08-03
yet another bash script :)

```
#!/bin/bash

function rn ()
{
  for i in "$1"/*; do
    echo "$i" | grep -q " "
    if [ "$?" -eq 0 ]; then
      newname=${i// /_}
      mv -b "$i" "$newname"
      if [ -d "$newname" ]; then
        rn "$newname"
      fi
    fi
  done
}

rn $1


```

it's faster than the previous one, but it's much slower than zmv.

```
time ./newscript ./

real	0m8.243s
user	0m2.780s
sys	0m4.953s

-------------------------------------------------------------------------

time ./zmv.zsh 

real	0m3.985s
user	0m1.267s
sys	0m2.333s

```

EDIT: and the final version :)

```
#!/bin/bash

function rn ()
{
  for i in "$1"/*; do
    if [[ "$i" =~ " "  ]]; then
      newname=${i// /_}
      mv -b "$i" "$newname"
      if [ -d "$newname" ]; then
        rn "$newname"
      fi
    fi
  done
}

rn $1

```

```
time ./script .

real	0m3.733s
user	0m1.297s
sys	0m2.183s

```

---

