---
title: "CloudInit not escaping left and right braces?"
date: 2012-01-06
forum: Ubuntu Cloud and Juju
---

### Post by zzzz8 on 2012-01-06
I'm using the Ubuntu 10.04 Amazon AMI.  In my UserData section of my CloudFormation template, I have the following content.  I'm trying to create an HTML file dynamically.  I have some CSS markup within the HTML file itself.  The CSS markup for different IDs and classes use left and right braces.  It seems as though Cloud-Init is not parsing the left and right braces within the JSON strings correctly?  I also tried escaping the left and right braces within the strings - and that did not work.

```
"UserData":{
                    "Fn::Base64":{
                        "Fn::Join":[
                            "\n",
                            [
                                "#cloud-config",
                                "\n",
                                "apt_update: true",
                                "apt_upgrade: true",
                                "runcmd:",
                                "- sudo apt-get -y install apache2",
                                "- cat << EOF > /var/www/index.html",
                                "- <!DOCTYPE html PUBLIC \"-//W3C//DTD XHTML 1.0 Strict//EN\" \"http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd\">",
                                "- <html xmlns=\"http://www.w3.org/1999/xhtml\">",
                                "- <head>",
                                "- <meta http-equiv=\"Content-Type\" content=\"text/html; charset=utf-8\" />",
                                "- <style type=\"text/css\">",
                                "- body {",
                                "- background-color: #F5F5F5;",
                                "- font-family: Arial, Helvetica, Verdana, sans-serif;",
                                "- font-size: 1.5em;",
                                "- margin: 0 auto;",
                                "- max-width: 960px;",
                                "- min-width: 960px;",
                                "- }",
                                "- #logo {",
                                "- margin-left: 1em;",
                                "- margin-top: 1em;",
                                "- }",
                                "- #downMessage {",
                                "- margin: 5em auto 0;",
                                "- max-width: 640px;",
                                "- min-width: 640px;",
                                "- }",
                                "- </style>",
                                "- </head>",
                                "- <body>",
                                "- <div id=\"logo\">",
                                "- </div>",
                                "- <div id=\"downMessage\">",
                                "- <p>The website is currently down for maintenance.</p>",
                                "- </div>",
                                "- </body>",
                                "- </html>",
                                "- EOF",
                                "- chown ubuntu:ubuntu /var/www/index.html",
                                "- chmod 644 /var/www/index.html"
                            ]
                        ]
                    }
                }
```

I'm getting the following errors in my Ubuntu system log:

```
File
"/usr/lib/python2.6/dist-packages/yaml/parser.py",
line 366, in parse_node
token.start_mark)
.parser.ParserError: while parsing a block node
expected the node content, but found '}'
in "<string>", line 24, column 3:
- }
^
self.current_event = self.state()
File
"/usr/lib/python2.6/dist-packages/yaml/parser.py",
line 403, in parse_indentless_sequence_entry
return self.parse_block_node()
ile
"/usr/lib/python2.6/dist-packages/yaml/parser.py",
line 260, in parse_block_node
return self.parse_node(block=True)
le "/usr/lib/python2.6/dist-packages/yaml/parser.py",
line 366, in parse_node
token.start_mark)
.parser.ParserError: while parsing a block node
expected the node content, but found '}'
in "<string>", line 24, column 3:
- }
^
ile parsing a block node
expected the node content, but found '}'
in "<string>", line 24, column 3:
- }
^
ile parsing a block node
expected the node content, but found '}'
in "<string>", line 24, column 3:
- }
^
ile parsing a block node
expected the node content, but found '}'
in "<string>", line 24, column 3:
- }
^
eback (most recent call last):
File "/usr/bin/cloud-init-cfg", line 56, in
<module>
main()
ile "/usr/bin/cloud-init-cfg", line 43, in main
cc = cloudinit.CloudConfig.CloudConfig(cfg_path)
le
"/usr/lib/python2.6/dist-packages/cloudinit/CloudConfi
g.py", line 42, in __init__
self.cfg = self.get_config_obj(cfgfile)
le
"/usr/lib/python2.6/dist-packages/cloudinit/CloudConfi
g.py", line 54, in get_config_obj
cfg=yaml.load(f.read())
le
"/usr/lib/python2.6/dist-packages/yaml/__init__.py",
line 58, in load
return loader.get_single_data()
le
"/usr/lib/python2.6/dist-packages/yaml/constructor.py"
, line 42, in get_single_data
node = self.get_single_node()
le
"/usr/lib/python2.6/dist-packages/yaml/composer.py",
line 36, in get_single_node
document = self.compose_document()
le
"/usr/lib/python2.6/dist-packages/yaml/composer.py",
line 55, in compose_document
node = self.compose_node(None, None)
le
"/usr/lib/python2.6/dist-packages/yaml/composer.py",
line 84, in compose_node
node = self.compose_mapping_node(anchor)
le
"/usr/lib/python2.6/dist-packages/yaml/composer.py",
line 133, in compose_mapping_node
item_value = self.compose_node(node, item_key)
le
"/usr/lib/python2.6/dist-packages/yaml/composer.py",
line 82, in compose_node
node = self.compose_sequence_node(anchor)
le
"/usr/lib/python2.6/dist-packages/yaml/composer.py",
line 110, in compose_sequence_node
while not self.check_event(SequenceEndEvent):
le "/usr/lib/python2.6/dist-packages/yaml/parser.py",
line 93, in check_event
self.current_event = self.state()
le "/usr/lib/python2.6/dist-packages/yaml/parser.py",
line 403, in parse_indentless_sequence_entry
return self.parse_block_node()
le "/usr/lib/python2.6/dist-packages/yaml/parser.py",
line 260, in parse_block_node
return self.parse_node(block=True)
le "/usr/lib/python2.6/dist-packages/yaml/parser.py",
line 366, in parse_node
token.start_mark)
.parser.ParserError: while parsing a block node
expected the node content, but found '}'
in "<string>", line 24, column 3:
- }
^
scape-client is not configured, please run
landscape-config.
```

I've tried taking out the CSS markup - and when I do that, the HTML file is created without any issues - so there's something wrong with the CSS markup in the JSON syntax...

---

