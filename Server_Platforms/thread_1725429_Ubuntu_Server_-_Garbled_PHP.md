---
title: "Ubuntu Server - Garbled PHP"
date: 2011-04-09
forum: Server Platforms
---

### Post by PhoenixIgnis on 2011-04-09
Hello, I am having an issue with a fairly updated Ubuntu LAMP Server and one particular user (for now). Like before when I made a topic, this may just be a client issue. But I was hoping to have some things cleared up for myself either way.

The problem:
The user loads a page and the contents end up garbled. This can include images or basic HTML delivered to the user.

Things I've tried with no success to solve his problem:
I had him switch from Firefox 3.6 to IE.
I had him switch from Firefox 3.6 to Firefox 4.
I disabled GZIP compression for php, html and png files.
I linked him a plain html page and a jpg image on my server was still corrupted.
Restarting his computer.
He switched to his desktop instead of laptop.

Typically the code ends up with ruined, random strings of the original content. Here is an example:
[http://i1025.photobucket.com/albums/y320/PuppetNightmares/Personal/garbled.jpg](http://i1025.photobucket.com/albums/y320/PuppetNightmares/Personal/garbled.jpg)

Now, I'd write this off as purely a client issue, but I've had something similar happen with another user in the past and I'd really like to know what's behind it, whether it's on my server's end or theirs.

Also, I often get messages like these in my logwatch:

  404 Not Found 
/images/menu%3Cul%3E/006-ei%3E%3Ca%20hre/: 1 Time(s)                  /images/menu%3Cul%3E/00ghtmares%3C/: 1 Time(s) 

Been that way for months.

Any advice on how to diagnose this issue is appreciated.

---

### Post by SeijiSensei on 2011-04-09
1)  What character set is in use?  Is the correct one?

2)  What do other people see who visit the same URL?  Is it fine for them but not for this person?  What does the actual HTML source look like in a browser where this page works? 

3)  What happens if you push the page through a [validator]("http://validator.w3.org/")?

4)  I presume all the bad HTML I see there (tags missing opening "<" or closing ">") is a symptom of the problem?  Otherwise it looks like poor coding, but without the generated HTML source to compare it to, it's impossible to say.

---

### Post by PhoenixIgnis on 2011-04-09
Thanks for the reply.

Nah it's purely some sort of "on delivery" problem. He's the only user of my site/server that currently has the issue. The actual source looks like this and works perfectly:

```
                  </tr>                   <tr>                    <th colspan="2">Current Party</th>                   </tr>                   <tr>                    <td><select style="background-image: none;" class="black_box" name="battle_party" onchange="document.getElementById('select_party').click();  ">                    <option value="0">No Party Selected</option>                    <option  value="1044998">Just Beat It</option><option  selected="selected" value="1090935">NoJ00</option><option  value="1090877">Cheeeta</option>                    </select></td>                     <td><input class="black_box" type="submit" name="heal" id="heal" value="Heal Party" /></td>                   </tr>                   <tr>                    <td>Healing Cost</td>                    <td><b>6<img style="margin: 0 0 0 5px" alt="healing cost" src="[images/icons/coins_s.png]("http://ubuntuforums.org/view-source:http://localhost/images/icons/coins_s.png")" /></b></td>                   </tr>                   <tr>                       <td><input type="submit" name="select_party" style="display: none;" id="select_party" value="Select" /></td>                   </tr>                   <tr>                    <th colspan="2">Click next battle to begin.</th>                   </tr>                   <tr>                      <td>Completed Battles <b>1</b></td>                      <td><input class="black_box" type="submit" name="next" id="next" value="Next Battle" /></td>                   </tr>                   <tr>                      <td>Consecutive Wins <b>1</b></td>                      <td><input class="black_box" type="submit" name="reset" id="reset" value="Reset Floor" /></td>                   </tr><tr>    <th colspan="2">     Supplies   </th> </tr>                   <tr>                                           <td><a href="[item_inventory.php]("http://ubuntuforums.org/view-source:http://localhost/item_inventory.php")">Items</a></td><td> <b >130/90</b></td>                   </tr>                   <tr>                                           <td><a href="[equip_inventory.php]("http://ubuntuforums.org/view-source:http://localhost/equip_inventory.php")">Equipment</a></td><td> <b >27/330</b></td>                   </tr>                   <tr>                                           <td><a href="[camp.php]("http://ubuntuforums.org/view-source:http://localhost/camp.php")">Creatures</a></td><td> <b >20/140</b></td>                   </tr>                   <tr>                                           <td><a href="[marble_inventory.php]("http://ubuntuforums.org/view-source:http://localhost/marble_inventory.php")">Marbles</a></td><td> <b >11/30</b></td>                   </tr>                 </table>                 </div>                 <div style="clear: both"></div>  </div> </form>             </div> <span class='server_data'><script type='text/javascript'> online_user_time(); </script>                                There are <b id='online_users'>0</b> players online. <a href='[/view_users.php]("http://ubuntuforums.org/view-source:http://localhost/view_users.php")'>Who's Online?</a>                           <br /> Server Time: <b>6:57 PM</b></span></div><div class="pw_ad"> </div> <!-- Google Analytics. --> <script type="text/javascript">    var _gaq = _gaq || [];   _gaq.push(['_setAccount', 'UA-19446695-3']);   _gaq.push(['_trackPageview']);    (function() {     var ga = document.createElement('script'); ga.type = 'text/javascript'; ga.async = true;     ga.src = ('https:' == document.location.protocol ? 'https://ssl' : 'http://www') + '.google-analytics.com/ga.js';     var s = document.getElementsByTagName('script')[0]; s.parentNode.insertBefore(ga, s);   })();  </script>          <div id="footer">           </div>       </div> </body> </html>
```

By the time it arrives to him, it gets corrupted this way randomly.  

[http://i1025.photobucket.com/albums/y320/PuppetNightmares/Personal/garbled.jpg](http://i1025.photobucket.com/albums/y320/PuppetNightmares/Personal/garbled.jpg)

I've been wondering if it might be some sort of packet issue between my server and him since it corrupts both images and html on his end.

The issue affects my phpbb forum for him also, and that isn't even code I wrote.

---

### Post by tgalati4 on 2011-04-10
What's your php.ini memory size?  Perhaps make it bigger?

---

### Post by PhoenixIgnis on 2011-04-10
Apparently that directive is set to -1 for no memory limit. 

; Maximum amount of memory a script may consume (128MB)
; [http://php.net/memory-limit](http://php.net/memory-limit)
memory_limit = -1

And as of today it is still happening to him and only him.

---

### Post by PhoenixIgnis on 2011-04-10
For anyone else having this problem, we isolated and concluded the user's router was at fault. When he upgraded the firmware it was a bit better, and when he bypassed it completely the problem was fixed.

Thanks to you two for the attempt at helping.

Edit: And sorry to double post by accident. I should have edited.

---

