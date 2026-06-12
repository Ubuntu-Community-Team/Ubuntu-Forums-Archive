---
title: "Why cant Firefox use the same proxies that Curl can?"
date: 2009-11-10
forum: Server Platforms
---

### Post by envis on 2009-11-10
i am not sure if anyone will have any idea about this, but i was trying to make a php script that was using Curl to test some proxies.

it works but the problem is i find that many proxies work on curl but when i try them in my firefox i get either an error message or a login menu or popup...

example, i dont know how long it will work but i have found this proxy, from USA: 208.100.40.34:80 when i use it with curl from the commant prompt on ubuntu like this: curl -x208.100.40.34:80 [http://abc.com/](http://abc.com/) i am able to fetch the page at abc.com or i can try some of my websites i can fetch any page.

in my PHP script i was doing:

function get_content_of_url($arandomproxy){
	$ohyeah = curl_init();
	curl_setopt($ohyeah, CURLOPT_FOLLOWLOCATION, 1);
    curl_setopt($ohyeah, CURLOPT_RETURNTRANSFER, 1);
    curl_setopt($ohyeah, CURLOPT_URL, 'http://mydomain.com/testfile_blah');
    curl_setopt($ohyeah, CURLOPT_COOKIEJAR, "cookie.txt");
    curl_setopt($ohyeah, CURLOPT_COOKIEFILE, "cookie.txt");
    curl_setopt($ohyeah, CURLOPT_USERAGENT, "Mozilla/5.0 (Windows; U; Windows NT 6.0; en-US; rv:1.9.1.5) Gecko/20091102 Firefox/3.5.5 (.NET CLR 3.5.30729)");
    curl_setopt($ohyeah, CURLOPT_TIMEOUT, 120);
    //curl_setopt($ohyeah, CURLOPT_SSL_VERIFYHOST, FALSE);
    //
curl_setopt($ohyeah, CURLOPT_SSL_VERIFYHOST, 2);
curl_setopt($ohyeah,CURLOPT_SSL_VERIFYPEER, 0);
curl_setopt($ohyeah,CURLOPT_CAINFO, NULL);
curl_setopt($ohyeah,CURLOPT_CAPATH, NULL); 

    //
    //
    //
	curl_setopt($ohyeah, CURLOPT_HTTPPROXYTUNNEL, TRUE);
	curl_setopt($ohyeah, CURLOPT_PROXY, $arandomproxy);
    $data = curl_exec($ohyeah);
    //echo htmlentities($data);
    curl_close($ohyeah);
    return $data;
}
$thefilereadbyprox=get_content_of_url("208.100.40.34:80");

and that works fine with that proxy, i am able to fetch any page and i have fetched pages that show my ip and it shows me the ip of the proxy....

but when i put that proxy in the setting of my firefox at home or opera, i get some login screen....

i have even tried setting up an ubuntu server at home to see if it was my home ip that was not accepted by the proxy, but no, even from home an ubuntu server is able to use curl through that proxy, but *human browsers give me that login screen when trying to go somewhere through that proxy..


so i dont know im just really blocked...  anyone has any idea how come??

i was hoping to test these proxies mostly for human usage not bot usage, or maybe the 2 in different categories i would have been sure a proxy that works for curl should have worked for firefox/opera/other and vice-versa but it doesnt appear to be the case, im confused, whats different?


#-o#-o#-o

---

### Post by envis on 2009-11-11
i think i found the solution

it was that line:

curl_setopt($ohyeah, CURLOPT_HTTPPROXYTUNNEL, TRUE);


made the proxy go tunnel or something... commenting out that line seems to make my curl get the same results as firefox will.

so some proxies would have worked with this line on, but without it it gets that login screen like a normal browser would

some other proxies too do not work with that line on and work with a browser and they do also work when i comment out that line.

---

