---
title: "conjobs"
date: 2008-05-17
forum: Server Platforms
---

### Post by xoligy on 2008-05-17
Hey all im new to linux, localhosts and php. Here is the problem im trying to work on a script that uses cronjobs, some of the pages wount show all the information until crons are active.

Now i did something with the crontab command (canna remember what) and by typing crontab -l i get this:

> xoligy@xoligy-desktop:~$ crontab -l
15 * * * * sh /home/public_html/Medi/cronfile/cron.php

I believe i got the address and command right but im unsure as im a newb :lolflag: anyhelp is appreciated :) oh it needs to update every 15mins believe i got that part right!

---

### Post by cdtech on 2008-05-17
That setup you have there will start the cronjob every 15 minutes after every hour. The way to set it up for every 15 minutes is to use the comma seperated values such as:

0,15,30,45 * * * * (command to be executed)

That will run every 15 minutes.

---

### Post by Oldsoldier2003 on 2008-05-17
> **cdtech said:**
> That setup you have there will start the cronjob every 15 minutes after every hour. The way to set it up for every 15 minutes is to use the comma seperated values such as:

0,15,30,45 * * * * (command to be executed)

That will run every 15 minutes.

0-59/15 * * * *   if you wanted it to run every 10 minutes 0-59/10  etc ...

---

### Post by cdtech on 2008-05-17
thanks Oldsoldier2003 for correcting me.

But what if I wanted to run it at 10 min after then 25 min after and then at 50 min after?

---

### Post by xoligy on 2008-05-18
Thanks for the responces, i have just deleted the old crontab and started a new one with the following settings

> xoligy@xoligy-desktop:~$ crontab -l
0,15,30,45 * * * * sh /home/public_html/Medi/cronfile/cron.php

This should "hopefully" run the file cron.php, but even with my old way it didnt look like it ran. Turns given at the start was 50 and after 48hrs there was still 50 :confused:

maybe its the file thats not working right i dunno lol

[PHP]<?	

	function defSort ($a, $b) {

    if ($a->DefenseAction == $b->DefenseAction) return 0;

    return ($a->DefenseAction > $b->DefenseAction) ? -1 : 1;

	}

	function atSort ($a, $b) {

    if ($a->StrikeAction == $b->StrikeAction) return 0;

    return ($a->StrikeAction > $b->StrikeAction) ? -1 : 1;

	}

	function covSort ($a, $b) {

    if ($a->CovertAction == $b->CovertAction) return 0;

    return ($a->CovertAction > $b->CovertAction) ? -1 : 1;

	}

	function rankFloat ($a, $b) {

    if ($a->RankFloat == $b->RankFloat) return 0;

    return ($a->RankFloat < $b->RankFloat) ? -1 : 1;

	}

	

	include "/home/xoligy/public_html/medi/vsys.php";

	deleteOldUsers();

	$users=getActiveUsers("ID, race, fortificationLevel, siegeLevel, currentSpySkill, trainedAttackSold, trainedAttackMerc, trainedDefSold, trainedDefMerc, untrainedSold, untrainedMerc, spies ");

	for ($i=0; $i<count($users);$i++){

		//print_r($users[$i]);print "<br>";

		$users[$i]->StrikeAction=getStrikeAction($users[$i]);

		$users[$i]->DefenseAction=getDefenseAction($users[$i]);

		$users[$i]->CovertAction=getCovertAction($users[$i]);

		$money=getUserIncome($users[$i]);

		updateUser($users[$i]->ID," gold = gold+'$money', attackTurns = attackTurns+1, untrainedSold=untrainedSold+currentUnitProduction ");

		//echo getStrikeAction($users[$i])."<br>";

		//echo getDefenseAction($users[$i])."<br>";

		//echo getCovertAction($users[$i])."<br>";

	}

	$users1=$users;

	usort($users1,"atSort");

	//echo "--------------users1---<br>";

	//print_r ($users1);

	$users2=$users;

	usort($users2,"defSort");

	//echo "--------------users2---<br>";

	//print_r ($users2);

	$users3=$users;

	usort($users3,"covSort");

	//echo "--------------users3---<br>";

	//print_r ($users3);

	

	for ($i=0;$i<count($users1);$i++){

		$usersA[$users1[$i]->ID]->ID=$users1[$i]->ID;

		$usersA[$users1[$i]->ID]->StrikeAction=$i+1;

	}

	for ($i=0;$i<count($users2);$i++){

		$usersA[$users2[$i]->ID]->DefenseAction=$i+1;

	}

	for ($i=0;$i<count($users3);$i++){

		$usersA[$users3[$i]->ID]->CovertAction=$i+1;

		$usersA[$users3[$i]->ID]->RankFloat=($usersA[$users3[$i]->ID]->StrikeAction+$usersA[$users3[$i]->ID]->DefenseAction+$usersA[$users3[$i]->ID]->CovertAction)/3;

	}

	usort($usersA,"rankFloat");

	for ($i=0;$i<count($usersA);$i++){

		//echo $usersA[$i]->RankFloat.";;";

		setUserRank($usersA[$i]->ID, $i+1, $usersA[$i]->StrikeAction, $usersA[$i]->DefenseAction , $usersA[$i]->CovertAction);

	}

	$q = mysql_query('select * from Mercenaries');

	if(mysql_num_rows($q) == 0){

		mysql_query('insert into Mercenaries(attackSpecCount, defSpecCount, untrainedCount, lastTurnTime) values(0,0,0,0)');

	}

	updateMercenary(" attackSpecCount=attackSpecCount+'{$conf['mercenaries_per_turn']}', defSpecCount =defSpecCount +'{$conf['mercenaries_per_turn']}', untrainedCount =untrainedCount +'{$conf['mercenaries_per_turn']}', lastTurnTime = '".time()."' ");

?>[/PHP]

---

### Post by gombadi on 2008-05-18
> 
0,15,30,45 * * * * sh /home/public_html/Medi/cronfile/cron.php


This tells cron to start a shell and then run the /home/public_html/Medi/cronfile/cron.php file as a shell script but it is php code.

You will need to change sh to the php interpreter so it can understand the contents of the php file.

Each time cron is running the file it should have been generating errors and cron should have been gathering them up and emailing them to the user running the cron job. Were you getting any emails?

---

### Post by xoligy on 2008-05-18
No, no emails but then i dont have any email type software on what would i need to install for that? All i put on for server use was the following command - "sudo tasksel install lamp-server" after that i installed phpmyadmin interface for easier use lol

As for changing the sh to php int, i take it i just do the same command but with php instead of sh? Sorry for being a pain, will save the book mark for future reference ;)

---

### Post by gombadi on 2008-05-18
Have a look in /var/mail directory. There should be a file for each user that has received email. If the cronjob is run as root then the root file should contain the email messages. Have a look around and you will find instructions on how to setup an email server if you want to.

Yes just change sh to php may work. There is a php5-cli package that you need for running php code from the command line. Not sure if it is installed with lamp-server or not. Try the command from the command line to make sure it works and then paste the same command into cron. May need the full path to the program because cron has a restricted PATH variable.

---

### Post by xoligy on 2008-05-18
Cheers mate seem to be getting somewhere now :)

> Warning: include(/home/xoligy/public_html/medi/vsys.php): failed to open stream: No such file or directory in /home/xoligy/public_html/Medi/cronfile/cron.php on line 19

Warning: include(): Failed opening '/home/xoligy/public_html/medi/vsys.php' for inclusion (include_path='.:/usr/share/php:/usr/share/pear') in /home/xoligy/public_html/Medi/cronfile/cron.php on line 19

Fatal error: Call to undefined function deleteOldUsers() in /home/xoligy/public_html/Medi/cronfile/cron.php on line 20


I believe that error is the because the folder name is Medi and i specified medi guess i'll see if it works in 10mins lol

---

### Post by xoligy on 2008-05-18
All sorted thanks to those that helped!

---

