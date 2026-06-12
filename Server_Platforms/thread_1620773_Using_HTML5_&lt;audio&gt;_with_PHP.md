---
title: "Using HTML5 &lt;audio&gt; with PHP"
date: 2010-11-13
forum: Server Platforms
---

### Post by jmrenner on 2010-11-13
Hello, recently I've been trying to create a basic HTML5 audio player that works by loading files dynamically through a php file.
For example:
[HTML]<audio src="play.php?songid=10" controls="controls" />[/HTML]
Very simple.
I'm using X-Sendfile as it supposedly is a much cleaner way to send files to the user. My php looks like this:
[PHP]<?php 
header('X-Sendfile: Holiday.ogg');
?>[/PHP]
I know I'm probably missing a lot of headers and such but it seems to work perfectly in firefox. In chrome, however, it fails. It will play for a bit but if you pause it before its completed loading, and press play again it won't play any sound. Any ideas?

---

