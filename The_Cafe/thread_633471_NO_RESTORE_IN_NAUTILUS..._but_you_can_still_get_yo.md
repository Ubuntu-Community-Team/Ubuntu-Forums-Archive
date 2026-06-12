---
title: "NO RESTORE IN NAUTILUS... but you can still get your music back"
date: 2007-12-06
forum: The Cafe
---

### Post by perljam on 2007-12-06
many of you have been victim to someone accidentally deleting music from, say.. rythmbox and not being able to restore some 14,000 odd songs to their original id3tag-related folders.

because of this, here is a perl script i whipped up to fix my own problem, there are a few problem with it, but it should be good for those who REALLY need it now. just be sure to change certain paths to suit you. when i find it, i'll post the fixed scripts here.

========================================
#!/usr/bin/perl

use MP3::Tag;

$allmp3s = `ls "/home/ackbar/toconvert/" | grep mp3 2>&1`;
@allmp3 = split "\n", $allmp3s;

for( $scrubs = 0; $scrubs <= $#allmp3; $scrubs++ ){
	print "@allmp3[$scrubs]";         @allmp3[$scrubs] =~ s/\n//;
$mp3 = MP3::Tag->new("/home/ackbar/toconvert/" . @allmp3[$scrubs]);
($title, $track, $artist, $album, $comment, $year, $gen ) =  $mp3->autoinfo();

	print "Artist -> ", $artist; print "\n";
	print "Album -> ", $album; print "\n";

	system( "mkdir -p /home/ackbar/org/\"$artist\"/\"$album\"/" );
	
	$dir = "/home/ackbar/org/$artist/$album/";


	system( "mv \"/home/ackbar/toconvert/" . @allmp3[$scrubs] . "\" \""  .  $dir . @allmp3[$scrubs] . "\"" );

}	
========================================

---

