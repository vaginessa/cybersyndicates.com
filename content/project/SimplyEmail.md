+++
title = "SimplyEmail"
description = "- Email recon made easy!"
date = 2016-11-18T02:13:50Z
author = "Alexander Rymdeko-Harvey"
+++
![alt text](https://simplyemail.org/img/se-logo-2.png "Logo Title Text 1")

# SimplyEmail

What is the simple email recon tool? This tool was based off the work of theHarvester and kind of a port of the functionality. This was just an expansion of what was used to build theHarvester and will incorporate his work but allow users to easily build Modules for the Framework. Which I felt was desperately needed after building my first module for theHarvester.

MAJOR CALLOUTS:
- @laramies - Developer of theHarvester tool https://github.com/laramies/theHarvester
- @CptJesus - Helped dev framework


Work Conducted by:
----------------------------------------------
* Alexander Rymdeko-Harvey [Twitter] @Killswitch-GUI -- [Web] [CyberSydicates.com](http://cybersyndicates.com)
* Keelyn Roberts [Twitter] @real_slacker007 -- [Web] [CyberSydicates.com](http://cybersyndicates.com)

<div class="github-card" data-github="killswitch-gui/SimplyEmail" data-width="400" data-height="153" data-theme="default"></div>
<script src="//cdn.jsdelivr.net/github-cards/latest/widget.js"></script>


## Scrape EVERYTHING - Simply 

Current Platforms Supported:
* Kali Linux 2.0
* Kali Linux 1.0
* Debian (deb8u3)

A few small benefits:
- Easy for you to write modules (All you need is 1 required Class option and you're up and running)
- Use the built in Parsers for rawest results
- Multiprocessing Queue for modules and Result Queue for easy handling of Email data 
- Simple integration  of theHarvester Modules and new ones to come
- Also the ability to change major settings fast without diving into the code

API Based Searches:
- When API based searches become available, no need to add them to the Command line
- API keys will be auto pulled from the SimpleEmail.ini, this will activate the module for use
 
## Get Started on Deb
Please RUN the simple Setup Bash script!
```Bash
# sh Setup.sh
or
# ./Setup.sh
```
## Get Started in Kali
Please RUN the simple Setup Bash script! 
NOTE: At the moment the up-streeam debian python-futures contain bugs within configparser / python-magic. This has been reported to KALI and debiab.
configparser bug in apt-get python-futures: https://bugs.kali.org/view.php?id=3245
SimplyEmail bug reported: https://github.com/killswitch-GUI/SimplyEmail/issues/11
```
FIX KALI BUG: 
# apt-get remove configparser
# apt-get remove python-magic
or 
# apt-get remove python-futures

Normal Setup
# ./Setup.sh
```
## Get Started on Mac OSX (At own risk)
```
Install brew:
https://coolestguidesontheplanet.com/installing-homebrew-on-os-x-el-capitan-10-11-package-manager-for-unix-apps/

$ sudo easy_install pip
$ sudo brew install libmagic
$ pip install python-magic
$ ./Setup.sh
```

### Standard Help
```
 ============================================================
 Current Version: v1.4.2 | Website: CyberSyndicates.com
 ============================================================
 Twitter: @real_slacker007 |  Twitter: @Killswitch_gui
 ============================================================
------------------------------------------------------------
   ______  ________                       __ __
 /      \/        |                     /  /  |
/$$$$$$  $$$$$$$$/ _____  ____   ______ $$/$$ |
$$ \__$$/$$ |__   /     \/    \ /      \/  $$ |
$$      \$$    |  $$$$$$ $$$$  |$$$$$$  $$ $$ |
 $$$$$$  $$$$$/   $$ | $$ | $$ |/    $$ $$ $$ |
/  \__$$ $$ |_____$$ | $$ | $$ /$$$$$$$ $$ $$ |
$$    $$/$$       $$ | $$ | $$ $$    $$ $$ $$ |
 $$$$$$/ $$$$$$$$/$$/  $$/  $$/ $$$$$$$/$$/$$/

------------------------------------------------------------
usage: SimplyEmail.py [-all] [-e company.com] [-l] [-t html / flickr / google]
                      [-s] [-n] [-verify] [-v] [--json json-emails.txt]

Email enumeration is a important phase of so many operation that a pen-tester
or Red Teamer goes through. There are tons of applications that do this but I
wanted a simple yet effective way to get what Recon-Ng gets and theHarvester
gets. (You may want to run -h)

optional arguments:
  -all                  Use all non API methods to obtain Emails
  -e company.com        Set required email addr user, ex ale@email.com
  -l                    List the current Modules Loaded
  -t html / flickr / google
                        Test individual module (For Linting)
  -s                    Set this to enable 'No-Scope' of the email parsing
  -n                    Set this to enable Name Generation
  -verify               Set this to enable SMTP server email verify
  -v                    Set this switch for verbose output of modules
  --json json-emails.txt
                        Set this switch for json output to specfic file
```

### Run SimplyEmail

Let's say your target is cybersyndicates.com
```python
./SimplyEmail.py -all -e cybersyndicates.com

or in verbose
./SimplyEmail.py -all -v -e cybersyndicates.com

or in verbose and no "Scope"
./SimplyEmail.py -all -v -e cybersyndicates.com -s

or with email verification
./SimplyEmail.py -all -v -verify -e cybersyndicates.com 

or with email verification & Name Creation
./SimplyEmail.py -all -v -verify -n -e cybersyndicates.com 

or json automation
./SimplyEmail.py -all -e cybersyndicates.com --json cs-json.txt
```
This will run ALL modules that are have API Key placed in the SimpleEmail.ini file and will run all non-API based modules. 

### List Modules SimpleEmail
```
root@kali:~/Tools/SimplyEmail# ./SimplyEmail.py -l
 ============================================================
 Current Version: v0.7 | Website: CyberSyndicates.com
 ============================================================
 Twitter: @real_slacker007 |  Twitter: @Killswitch_gui
 ============================================================
------------------------------------------------------------
   ______  ________                       __ __
 /      \/        |                     /  /  |
/$$$$$$  $$$$$$$$/ _____  ____   ______ $$/$$ |
$$ \__$$/$$ |__   /     \/    \ /      \/  $$ |
$$      \$$    |  $$$$$$ $$$$  |$$$$$$  $$ $$ |
 $$$$$$  $$$$$/   $$ | $$ | $$ |/    $$ $$ $$ |
/  \__$$ $$ |_____$$ | $$ | $$ /$$$$$$$ $$ $$ |
$$    $$/$$       $$ | $$ | $$ $$    $$ $$ $$ |
 $$$$$$/ $$$$$$$$/$$/  $$/  $$/ $$$$$$$/$$/$$/

------------------------------------------------------------
 [*] Available Modules are:

  1)  Modules/HtmlScrape.py   
  2)  Modules/PasteBinSearch.py
  3)  Modules/ExaleadSearch.py
  4)  Modules/SearchPGP.py    
  5)  Modules/ExaleadXLSXSearch.py
  6)  Modules/ExaleadDOCXSearch.py
  7)  Modules/OnionStagram.py 
  8)  Modules/GooglePDFSearch.py
  9)  Modules/RedditPostSearch.py
  10) Modules/AskSearch.py    
  11) Modules/EmailHunter.py  
  12) Modules/WhoisAPISearch.py
  13) Modules/Whoisolgy.py    
  14) Modules/GoogleDocxSearch.py
  15) Modules/GitHubUserSearch.py
  16) Modules/YahooSearch.py  
  17) Modules/GitHubCodeSearch.py
  18) Modules/ExaleadPDFSearch.py
  19) Modules/GoogleSearch.py 
  20) Modules/FlickrSearch.py 
  21) Modules/GoogleDocSearch.py
  22) Modules/CanaryBinSearch.py
  23) Modules/ExaleadDOCSearch.py
  24) Modules/GoogleXLSXSearch.py
  25) Modules/GitHubGistSearch.py
```
## API Modules and Searches
API based searches can be painful and hard to configure. The main aspect of SimplyEmail is to easily integrate these aspects, while not compromising the ease of using this tool. Using the configuration file, you can simply add your corresponding API key and get up and running. Modules are automatically identified as API based searches, checks if the corresponding keys are present and if the keys are present it will run the module. 

### Canar.io API Search
Canario is a service that allows you to search for potentially leaked data that has been exposed on the Internet. Passwords, e-mail addresses, hostnames, and other data have been indexed to allow for easy searching.

Simply Register for a key here:
[canar.io] (https://canar.io/register/) or https://canar.io/register/
Place the key in the SimplyEmail.ini at [APIKeys] section, the module will now initiate when the --all flag is user of the -t.


## Name Generation
Some times SimplyEmail will only find the standard email addresses or just a few emails. In this case email creation may be your saving grace. Using name generation can allow you not only scrape names from diffrent sites but allow you to auto detect the format to some accuracy. 

### LinkedIn Name Generation
Using Bing and work from PhishBait I was able to implement LinkedIn name lookups from the company name. 

### Connect6.com Name Generation
Connect6 is also a great source for names, and also a bit flaky to find the source. Using a AutoUrl function I built I do attempt to find the correct URL for you. If not I provide you with a few more to pick from.

```
 ============================================================
 Current Version: v1.1 | Website: CyberSyndicates.com
 ============================================================
 Twitter: @real_slacker007 |  Twitter: @Killswitch_gui
 ============================================================
 [*] Now Starting Connect6 Scrape:
 [*] SimplyEmail has attempted to find correct URL for Connect6:
     URL detected: www.connect6.com/Vfffffff,%20LLC/c 
 [>] Is this URL correct?: n
    Potential URL: www.connect6.com/Vffffffff,%20LLC/c 
    Potential URL: www.connect6.com/fffffff/p/181016043240247014147078237069133079124017210127108009097255039209172025193089206212192166241042174198072085028234035215132077249038065254013074 
    Potential URL: www.connect6.com/Cfffff/p/034097047081090085111147210185030172009078049169022098212236211095220195001177030045187199131226210223245205084079141193247011181189036140240023 
    Potential URL: www.connect6.com/Jfffffff/p/102092136035048036136024218227078226242230121102078233031208236153124239181008089103120004217018 
    Potential URL: www.connect6.com/Adam-Salerno/p/021252074213080142144144173151186084054192089124012168233122054057047043085086050013217026242085213002224084036030244077024184140161144046156080 
 [!] GoogleDork This: site:connect6.com "Vfffff.com"
 [-] Commands Supported: (B) ack - (R) etry
 [>] Please Provid a URL: b

```

## Verifying Emails via target SMTP server:
More often than not you will have at least a few invalid emails gathered from recon. SimplyEmail now supports
the ability to verify and check if the email is valid.
- Looks up MX records
- Sorts based on priority 
- Checks if SMTP server will respond other than 250
- If the server is suitable, checks for 250 codes
- Outputs a (.txt) file with verified emails. 

```
============================================================
 Curent Version: v1.0 | Website: CyberSyndicates.com
 ============================================================
 Twitter: @real_slacker007 |  Twitter: @Killswitch_gui
 ============================================================
 [*] Email reconnaissance has been completed:

    Email verification will allow you to use common methods
    to attempt to enumerate if the email is valid.
    This grabs the MX records, sorts and attempts to check
    if the SMTP server sends a code other than 250 for known bad addresses

 [>] Would you like to verify email(s)?: y
 [*] Attempting to resolve MX records!
 [*] MX Host: gmail-smtp-in.l.google.com.
 [*] Checking for valid email: alwathiqlegaltranslation@gmail.com
 [!] Email seems valid: alwathiqlegaltranslation@gmail.co
```

## Understanding Reporting Options:
One of the most frustrating aspects of Pen-testing is the tools' ability
to report the findings and make those easily readable. This may be for the data
provided to a customer or just the ability to report on source of the data.

So I'm making it my goal for my tools to take that work off your back and make it as simple as possible!
Let's cover the two different reports generated.
### Text Output:
With this option results are generated and appended to a running text file called Email_List.txt. 
this makes it easy to find past searches or export to tool of choice. Example:
```
  ----------------------------------
  Email Recon: 11/11/2015 05:13:32
  ----------------------------------
bo@mandiant.com
in@mandiant.com
sc@mandiant.com
je@mandiant.com
su@mandiant.com
----------------------------------
  Email Recon: 11/11/2015 05:15:42
  ----------------------------------
bo@mandiant.com
in@mandiant.com
sc@mandiant.com
je@mandiant.com
su@mandiant.com
```
### JSON Output
using the ```--json test.txt``` flag will alow you to output standard JSON text file for automation needs. This can be currently used with the email scraping portion only, maybe name generation and email verification to come. These helpers will be soon in the SQL DB and API for more streamline automation. Example output:
```
{
    "current_version": "v1.4.1", 
    "data_of_collection": "26/06/2016", 
    "domain_of_collection": "---SNIP---", 
    "email_collection_count": 220, 
    "emails": [
        {
            "collection_data": "26/06/2016", 
            "collection_time": "18:47:42", 
            "email": "---SNIP---", 
            "module_name": "Searching PGP"
        }, 
       ---SNIP---
        {
            "collection_data": "26/06/2016", 
            "collection_time": "18:51:46", 
            "email": "---SNIP---", 
            "module_name": "Exalead PDF Search for Emails"
        }
    ], 
    "time_of_collection": "18:53:04", 
    "tool_of_collection": "SimplyEmail"
}
```
### HTML Output:
As I mentioned before a powerful function that I wanted to integrate was the ability to produce a visually appealing and rich report for the user and potentially something that could be part of data provided to a client. Please let me know with suggestions! 
#### Email Source:
![Alt text](/bootstrap-3.3.5/Screen Shot 2015-11-11 at 5.27.15 PM.png?raw=true "Report")
#### Email Section:
- Html report now shows Alerts for Canary Search Results!
![Alt text](/bootstrap-3.3.5/Screen Shot 2015-11-11 at 5.27.31 PM.png?raw=true "Report Html")

## Current Email Evasion Techniques
- The following will be built into the Parser Soon:
- shinichiro.hamaji _at_ gmail.com
- shinichiro.hamaji _AT_ gmail.com
- simohayha.bobo at gmail.com
- "jeffreytgilbert" => "gmail.com"
- felix021 # gmail.com
- hirokidaichi[at]gmail.com
- hirokidaichi[@]gmail.com 
- hirokidaichi[#]gmail.com
- xaicron{ at }gmail.com
- xaicron{at}gmail.com
- xaicron{@}gmail.com
- xaicron(@)gmail.com
- xaicron + gmail.com
- xaicron ++ gmail.com
- xaicron ## gmail.com
- bekt17[@]gmail.com
- billy3321 -AT- gmail.com
- billy3321[AT]gmail.com
- ybenjo.repose [[[at]]] gmail.com
- sudhindra.r.rao (at) gmail.com
- sudhindra.r.rao nospam gmail.com
- shinichiro.hamaji (.) gmail.com
- shinichiro.hamaji--at--gmail.com

#### TODO:
```
Modules Under Dev:
-----------------------------
( ) StartPage Search (can help with captcha issues)
( ) Searching SEC Data
( ) PwnBin Search 
( ) Past Data Dumps
( ) psbdmp API Based and non Alert

Framework Under Dev:
-----------------------------
( ) New Parsers to clean results
( ) Fix import errors with Glob
( ) Add in "[@]something.com" to search Regex and engines
( ) Add Threading/Multi to GitHub Search
( ) Add Source of collection to HTML Output

Current Issues:
-----------------------------
( ) PDF miner Text Extraction Error
( ) Verify Emails function and only one name list raises errors

```

[![Build Status](https://travis-ci.org/killswitch-GUI/SimplyEmail.svg?branch=master)](https://travis-ci.org/killswitch-GUI/SimplyEmail)
[![Code Health](https://landscape.io/github/killswitch-GUI/SimplyEmail/master/landscape.svg?style=flat)](https://landscape.io/github/killswitch-GUI/SimplyEmail/master)
[![Codacy Badge](https://api.codacy.com/project/badge/grade/3b8a338b659e425e9b4e1db9eace61d7)](https://www.codacy.com/app/iamfree2009/SimplyEmail)
[![Coverage Status](https://coveralls.io/repos/github/killswitch-GUI/SimplyEmail/badge.svg?branch=Version-1.4)](https://coveralls.io/github/killswitch-GUI/SimplyEmail?branch=Version-1.4)