---
title: "How to install Gyazo on Ubuntu"
date: 2011-04-03
forum: Tutorials
---

### Post by laugh1 on 2011-04-03
[Gyazo](http://www.gyazo.com) is a screenshot-taker that takes a screenshot of a custom area. It is only made for Windows, but can be coded for Ubuntu to. Here is what you do:

1. Install Imagemagick in the Software Center
[img]http://gyazo.com/4f765aed0f8b6e0e1e12bdeaff273443.png[/img]

2. Open the Terminal and type "sudo apt-get install ruby" without the quotes. Let it install.
[img]http://gyazo.com/af0021fa7fb51982a97f2e26c0ab5d75.png[/img]

3. Now open gedit and paste this code in:
```
#!/usr/bin/env ruby 

# setting 
browser_cmd = 'firefox' 
clipboard_cmd = 'xclip' 
proxy_addr = nil 
proxy_port = nil 

require 'net/http' 

# get id 
idfile = ENV['HOME'] + "/.gyazo.id" 

id = '' 
if File.exist?(idfile) then 
  id = File.read(idfile).chomp 
end 

# capture png file 
tmpfile = "/tmp/image_upload#{$$}.png" 
imagefile = ARGV[0] 

if imagefile && File.exist?(imagefile) then 
  system "convert #{imagefile} #{tmpfile}" 
else 
  system "import #{tmpfile}" 
end 

if !File.exist?(tmpfile) then 
  exit 
end 

imagedata = File.read(tmpfile) 
File.delete(tmpfile) 

# upload 
boundary = '----BOUNDARYBOUNDARY----' 

HOST = 'gyazo.com' 
CGI = '/upload.cgi' 
UA   = 'Gyazo/1.0' 

data = <<EOF 
--#{boundary}\r 
content-disposition: form-data; name="id"\r 
\r 
#{id}\r 
--#{boundary}\r 
content-disposition: form-data; name="imagedata"; filename="gyazo.com"\r 
\r 
#{imagedata}\r 
--#{boundary}--\r 
EOF 

header ={ 
  'Content-Length' => data.length.to_s, 
  'Content-type' => "multipart/form-data; boundary=#{boundary}", 
  'User-Agent' => UA 
} 

Net::HTTP::Proxy(proxy_addr, proxy_port).start(HOST,80) {|http| 
  res = http.post(CGI,data,header) 
  url = res.response.to_ary[1] 
  puts url 
  if system "which #{clipboard_cmd} >/dev/null 2>&1" then 
    system "echo -n #{url} | #{clipboard_cmd}" 
  end 
  system "#{browser_cmd} #{url}" 

  # save id 
  newid = res.response['X-Gyazo-Id'] 
  if newid and newid != "" then 
    if !File.exist?(File.dirname(idfile)) then 
      Dir.mkdir(File.dirname(idfile)) 
    end 
    if File.exist?(idfile) then 
      File.rename(idfile, idfile+Time.new.strftime("_%Y%m%d%H%M%S.bak")) 
    end 
    File.open(idfile,"w").print(newid) 
  end 
}
```
The line that says **browser_cmd = 'firefox'** will open Firefox so if you want it to open Chromium instead replace it with **browser_cmd = 'chromium-browser'**

Now save it as gyazo.rb

4. Right-click gyazo.rb and click Properties. And under Permissions check the Execution box.
[img]http://gyazo.com/2fb838e2ce670c13eb3a1919bafa56b4.png[/img]

5. Drag it to your navbar on the top and when you want to take a picture just click it! 
[img]http://gyazo.com/0f8baa6fc1dea52ddd55a2a82f294c03.png[/img]

Enjoy!

---

### Post by dannyboy79 on 2013-01-13
i am trying to do this and it doesn't appear to be working. I am using Xubuntu 12.04 and there is 2 different versions of ruby, there's 1.8 and 1.9.1, I installed the latest one. I changed the execute bit on the file but when I double click it nothing happens.  If I run it from the command line, it returns this:

```
/usr/local/bin/gyazo.rb:82: can't find string "EOF" anywhere before EOF
/usr/local/bin/gyazo.rb:43: syntax error, unexpected $end, expecting tSTRING_CONTENT or tSTRING_DBEG or tSTRING_DVAR or tSTRING_END
data = <<EOF 
            ^

```

Can you help please?

---

