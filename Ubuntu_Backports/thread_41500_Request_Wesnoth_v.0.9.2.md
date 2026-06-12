---
title: "Request: Wesnoth v.0.9.2"
date: 2005-06-13
forum: Ubuntu Backports
---

### Post by lotusleaf on 2005-06-13
[Wesnoth](http://www.wesnoth.org/) v.[0.9.2](http://www.wesnoth.org/forum/viewtopic.php?t=6228) - released: 06-06-05

Of course 0.9.2 appears to be *required* to connect to the official Multiplayer server. Looks like a lot of changes, according to the changelog:

> "Version 0.9.2:
 * user interface improvements:
   * sped up frame rate when scrolling the map
   * connecting to a server now shows dialog that allows the user to cancel
     the connection rather than blocking (#12614)
   * sped up help
   * added hotkey for cycle to previous unit (shift-N) (part of #10703)
   * added hotkey for hold position (shift-space) (patch 3994)
   * made the right Command key on Mac OS X work like the left one
   * made menu widgets sortable
   * made network dialogs show progress of data transfers again
   * added display of unit defense over the terrain when choosing move
   * added visual cue for movement in specific terrain when choosing move
   * added %-to-kill to Damage Calculations
   * fixed female units not appearing in help (broken since 0.9.0)
   * added support for unit portraits in help (forum thread 6017)
   * reduced required width of weapon area in help
   * fixed items appearing in traits description (#12603)
   * preserve trait ordering to distinguish quick,resilient and resilient,quick
   * improved layout of objectives dialog
   * made the text of disabled buttons grayed out
   * made room for observers in DFool theme (#13027)
   * added clock to DFool theme (#10650)
   * added Experimental theme
   * tweaked multiplayer lobby
   * improved position and size of 'users' menu in multiplayer lobby (#13120)
   * selecting colors for multiplayer sides now works correctly (#13255)
   * typing a chat message quickly no longer lags the game (#12097)
   * pasting multiline text now discards lines after the first (#12282)
   * better checking for 'control' command arguments in multiplayer (#13086)
   * added 'Advanced' preferences: 'binary save files', 'show combat'
   * fixed village name being shown over shroud (#10690)
   * made ordering of terrain data consistent (#10665)
   * display error if save cannot be completed (eg. disk full) (#13232)
   * fixed halo position when unit is in water (#12493)
   * fixed titlescreen background disappearing on switch to fullscreen (#11863)
   * disabled mousewheel scrolling during combat and unit movement (#12021)
   * fixed pathfinding issues with respect to unreachable hexes (#11480, #13295)
 * campaign improvements:
   * Eastern Invasion:
     * Unexpected Appearance: fixed Dacyn not being [recall]-ed (#12830)
     * Evacuation: units left on the wrong side of river now really die (#10619)
     * Northern Outpost: killing enemies in "wrong" order is now a win (#12922)
     * Northern Outpost: added a Holy Water bottle
     * Captured: fixed bugs (#10512, #12998), but replaced scenario anyway
     * Drowned Plains: new map and scenario modification, bug fixed (#13013)
   * Heir to the Throne:
     * Siege of Elensefar: fixed thieves not appearing (forum thread 5719)
   * Son of the Black Eye:
     * prevented the shamans from being recallable (#11932)
     * Siege of Barag Gor: killing enemy leader is no longer a win
     * End of Peace: increased turn limit 24 -> 26 due to Lieutenant upgrade
     * Desert of Death: fixed invalid type=RogueAssassin on Hard
     * removed duplicate file inclusion - campaign should now start faster
     * more accurate difficulty labels
     * Toward Mountains of Haag: fixed enemy making "never pushed so far" speech
 * new units
   * added Drake Warden, Hurricane Drake and Drake Blademaster
 * unit balancing and modifications: 
   * slow now affects units with 2 or more attacks (not just 1 remaining)
   * slow now works with berserk and is persistent across berserk rounds
   * changed Lieutenant attack from 6-3 to 9-3
   * reduced Fencer cost from 18 to 16
   * changed Iron Mauler attack from 22-2 to 25-2
   * changed Soulless attack from 7-2 to 7-3
   * changed Soulless attack from plague to plague(Walking Corpse)
   * Walking Corpse created by plague can advance to Soulless again (#13056)
   * reduced Skeleton Archer cost from 15 to 14
   * changed Skeletal Dragon resistances (only used in Eastern Invasion)
   * tweaked Watch Tower, Pirate Galleon and Transport Galleon and removed
     their multihex attacks (only used as real units in Son of the Black Eye)
   * reduced Dwarvish Fighter cost from 17 to 16
   * reduced Dwarvish Fighter line Axe (blade) damage by 1 point 
   * reduced Dwarvish Thunderer cost from 19 to 17
   * reduced Gryphon Rider cost from 25 to 24
   * Dwarvish Ulfserker stats reverted to those from version 0.8.11
   * increased Thief cost from 12 to 13
   * changed Elvish Lord and Elvish High Lord's ranged attack from fire to cold
   * changed Elvish Ranger meele attack from 7-4 to 7-3
   * changed Elvish Avenger meele attack from 10-4 to 9-4
   * increased Walking Corpse cost from 5 to 6
   * trolls can no longer get "intelligent" random trait
   * increased Troll Whelp experience needed to advance from 32 to 33 XP
   * increased Troll experience needed to advance from 52 to 60 XP
   * Goblin Knight -> Direwolf Rider upgrade reduced from 150 to 65 XP
   * added flaming arrow to orcish archer line as a new attack
   * reduced Saurian Skirmisher movement to 6, increased its cost from 14 to 15
   * changed Drake Gladiator from 65 to 59 HP
   * changed Drake Gladiator pierce resistance from 10% to -10%
   * changed Drake Slasher from 59 to 65 HP
   * changed Drake Slasher pierce resistance from -10% to 10%
   * increased Drake Slasher and Drake Gladiator cost to 45 
 * Doc Paterson's modifications to the MP map catalogue
   * added "Divide and Conquer", "Silverhead Crossing", "Meteor Lake",
     "Den of Onis", "Hamlets", "Hornshark Island", "Sulla's Ruins",
     "1v1v1Hex" (3p), "Lagoon" (4p), "The Wilderlands" (4p),
     "3-player Morituri", "3-player Blitz (Triple Blitz)"
   * removed "Broken Bridge", "Battle For Weslin Bridge",
     "Princess's Battlefield", "Three Rivers", "The Isles of the Damned",
     "The Isle of Anduin", "Dwarven Wasteland" 
 * unit graphics and sound improvements:
   * new death animations for: Ancient Lich, Ancient Wose, Arch Mage,
     Assassin, Bandit, Battle Princess, Blood Bat, Bone Shooter, Bowman,
     Cavalier, Cavalryman, Cave Spider, Chocobone, Cockatrice,
     Commander, Cuttle Fish, Dark Adept, Dark Queen, Dark Spirit,
     Deathblade, Death Knight, Deathmaster, Demilich, Direwolf Rider,
     Dragoon, Duelist, Draug, Drake Burner, Drake Clasher, Drake Fighter,
     Fire Drake
   * new or modified graphics for Dragoon, Dwarvish Dragonguard,
     Elvish High Lord, Elvish Lord, Halberdier, Lady Parandra, Noble Lord,
     Royal Guard, Soulshooter, Swordsman
   * fixed several image files being referred to by wrong name
   * new Soulless variation images
   * added flaming arrow images
 * language and i18n:
   * language fixes and polishing (English) (also fixed #12613, #10714)
   * updated MANUAL
   * new translations: Serbian
   * updated translations: Afrikaans, British English, Catalan, Chinese,
     Czech (#12864), Estonian, Finnish, French, German (also fixed
     #13147), Greek, Hungarian, Italian, Japanese, Polish, Russian,
     Slovenian, Spanish, Swedish, Turkish
   * updated gettext support to GNU gettext 0.14.4
   * removed the intl/ directory, since libintl is now widespread enough
     for gettextize to default to not installing it
 * WML improvements:
   * new WML preprocessor, allows for nested parentheses in macros (#10995)
   * note= attribute for [objectives], shown as footer, eg. for hints (#12927)
   * increase_attacks= attribute of [effect] now allows percentages (#13033)
   * new [random] representation as list allows complex scenarios to be saved
     (forum thread 5659)
   * better diagnostics on parsing: show file inclusion sequence
   * added [scroll_to] (patch #3388, forum thread 3235)
   * added [advancefrom] (patch #3625, forum thread 4186)
   * [recall] tag can now work even if the recruiter is not in a keep
     (#10543, #11735, #12974)
   * next_scenario: tentative start of MP campaign support
   * tidied up game.cfg and traits.cfg; game startup should now be faster
 * editor improvements:
   * fixed editor file chooser when starting directory has many files (#11698)
   * the starting position in the editor now starts counting from 1 (#10625)
 * improvements and bug fixes of the logging system
 * fixed replays with idle_ai, as seen in user scenario Rebellion (#12943)
 * saving during an AI unit's turn no longer makes that unit disappear (#13023)
 * fixed Windows build crashing when trying to recruit units (#12926)
 * tutorial start and end scenario savegames can now be loaded (#10332)
 * various bug fixes and code cleanups (including #13264 #12954 #12734 #13263)" - [quote source](http://savannah.nongnu.org/cgi-bin/viewcvs/wesnoth/wesnoth/changelog?rev=HEAD)

---

### Post by Seth on 2005-06-14
[QUOTE=lotusleaf][Wesnoth](http://www.wesnoth.org/) v.[0.9.2](http://www.wesnoth.org/forum/viewtopic.php?t=6228) - released: 06-06-05

Of course 0.9.2 appears to be *required* to connect to the official Multiplayer server. Looks like a lot of changes, according to the changelog:

 - [quote source](http://savannah.nongnu.org/cgi-bin/viewcvs/wesnoth/wesnoth/changelog?rev=HEAD)[/QUOTE]
 Here you are, please let me know how it works for you :)
But... look at that CVS head, there'll be another version soon :/

[http://sethkinast.com/ubuntu/hoary/backports/wesnoth_0.9.2-1~5.04ubp1_i386.deb](http://sethkinast.com/ubuntu/hoary/backports/wesnoth_0.9.2-1~5.04ubp1_i386.deb)
[http://sethkinast.com/ubuntu/hoary/backports/wesnoth-data_0.9.2-1~5.04ubp1_all.deb](http://sethkinast.com/ubuntu/hoary/backports/wesnoth-data_0.9.2-1~5.04ubp1_all.deb)
[http://sethkinast.com/ubuntu/hoary/backports/wesnoth-editor_0.9.2-1~5.04ubp1_i386.deb](http://sethkinast.com/ubuntu/hoary/backports/wesnoth-editor_0.9.2-1~5.04ubp1_i386.deb)
[http://sethkinast.com/ubuntu/hoary/backports/wesnoth-ei_0.9.2-1~5.04ubp1_all.deb](http://sethkinast.com/ubuntu/hoary/backports/wesnoth-ei_0.9.2-1~5.04ubp1_all.deb)
[http://sethkinast.com/ubuntu/hoary/backports/wesnoth-httt_0.9.2-1~5.04ubp1_all.deb](http://sethkinast.com/ubuntu/hoary/backports/wesnoth-httt_0.9.2-1~5.04ubp1_all.deb)
[http://sethkinast.com/ubuntu/hoary/backports/wesnoth-music_0.9.2-1~5.04ubp1_all.deb](http://sethkinast.com/ubuntu/hoary/backports/wesnoth-music_0.9.2-1~5.04ubp1_all.deb)
[http://sethkinast.com/ubuntu/hoary/backports/wesnoth-server_0.9.2-1~5.04ubp1_i386.deb](http://sethkinast.com/ubuntu/hoary/backports/wesnoth-server_0.9.2-1~5.04ubp1_i386.deb)
[http://sethkinast.com/ubuntu/hoary/backports/wesnoth-sotbe_0.9.2-1~5.04ubp1_all.deb](http://sethkinast.com/ubuntu/hoary/backports/wesnoth-sotbe_0.9.2-1~5.04ubp1_all.deb)
[http://sethkinast.com/ubuntu/hoary/backports/wesnoth-tdh_0.9.2-1~5.04ubp1_all.deb](http://sethkinast.com/ubuntu/hoary/backports/wesnoth-tdh_0.9.2-1~5.04ubp1_all.deb)
[http://sethkinast.com/ubuntu/hoary/backports/wesnoth-trow_0.9.2-1~5.04ubp1_all.deb](http://sethkinast.com/ubuntu/hoary/backports/wesnoth-trow_0.9.2-1~5.04ubp1_all.deb)

---

### Post by jdong on 2005-06-14
Not in Breezy  ](*,)

---

### Post by Seth on 2005-06-14
[QUOTE=jdong]Not in Breezy  ](*,)[/QUOTE]
 Well we can fix that ;)

/me scuttles off

There are no Ubuntu-specific changes to Wesnoth, however, so this is what will / would show up in Breezy anyways, a direct yoink from upstream. This early in the game I don't think it is inappropriate to backport from upstream, as a newer version will enter Breezy universe before the freeze.

---

### Post by lotusleaf on 2005-06-14
[QUOTE=Seth]Here you are, please let me know how it works for you :)[/quote]

Awesome! Thanks very much Seth! :) Will this be available on the backports mirrors as well for those who don't read the forums here? 

> But... look at that CVS head, there'll be another version soon :/

True... but thanks to you, we now have the latest version to enjoy without having to compile it ourselves! :) Thanks again! :)

---

### Post by Seth on 2005-06-14
[QUOTE=lotusleaf]Awesome! Thanks very much Seth! :) Will this be available on the backports mirrors as well for those who don't read the forums here? 



True... but thanks to you, we now have the latest version to enjoy without having to compile it ourselves! :) Thanks again! :)[/QUOTE]
 Because this package isn't in Breezy, I doubt it is condoned as backport-mirror-worthy. I'll see about getting MOTU to put .9.3 in universe and then maybe it'll be commitable.

Don't I recognize you from suseforums? Get tired of SuSE? I did too :-P

---

### Post by lotusleaf on 2005-06-14
[QUOTE=Seth]Because this package isn't in Breezy, I doubt it is condoned as backport-mirror-worthy. I'll see about getting MOTU to put .9.3 in universe and then maybe it'll be commitable.[/quote]

Sounds good Seth, thanks again for your efforts, it's appreciated! :)

> Don't I recognize you from suseforums? Get tired of SuSE? I did too :-P

Yup and yup :) Using SUSE was fun for awhile but I eventually grew tired of using RPM based distros and waiting for the next version of SUSE to be released for free. Ubuntu is a hell of a lot of fun to use and the community here is great! :)

---

