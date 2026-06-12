---
title: "ffmpeg with xampp"
date: 2009-12-19
forum: Server Platforms
---

### Post by duleep on 2009-12-19
how to write php code for get video thumbnails using ffmpeg 

i used this code but not working:(
[php]
<?php
convertToFlv( "some-video-input.avi", "output.jpg" );
function convertToFlv( $input, $output ) {
    $command = "ffmpeg -v 0 -y -i $input -vframes 1 -ss 5 -vcodec mjpeg -f rawvideo -s 286x160 -aspect 16:9 $output ";
    shell_exec( $command );
}
?>[/php]

---

