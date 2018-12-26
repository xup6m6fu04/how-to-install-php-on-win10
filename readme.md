<p>第一次在 win10 這個可怕的系統下安裝開發環境</p>
<p>參考文章如下 : https://drivemarketing.ca/en/blog/installing-composer-on-windows-10/</p>

<p><strong>Preface</strong></p>

<p>First off, I have had a <em>very</em> long night. I had to get Composer installed on my computer in order to complete a mandate for a client and I ran into more stumbling blocks than I care to admit. In the end, though, I managed to learn a lot about how to install Composer on a Windows 10 machine and was able to perform a second install on my office desktop in about ten minutes.</p>

<p>The purpose of my writing this blog entry is to (hopefully) help any of you out there who have run into the same problem.</p>

<p>&nbsp;</p>

<p><strong>What Is Composer and Why Should I Care?</strong></p>

<p>These are good questions. In fact, these are questions that, until recently, I was asking myself. I don&rsquo;t have an answer yet, but these are good questions to ask &hellip; I guess &hellip;</p>

<p>&nbsp;</p>

<p><strong>The Good Stuff</strong></p>

<p>Ok, so how exactly do you install Composer on Windows? What&rsquo;s the big deal? If you&rsquo;re reading this, very likely, you&rsquo;ve already tried it yourself and run into stumbling blocks and got stuck. The reason it took me so long last night is because I had to try a bunch of things that ended up being dead-ends. The list of steps below is the boiled down version of what I managed to figure out through much trial and error. These are also the only steps I took in order to install Composer on my second machine this morning. Best of luck!</p>

<ol>
	<li>Download and Setup PHP
	<ol style="list-style-type:lower-alpha;">
		<li>Download PHP for Windows &ndash; Go to http://windows.php.net/download/ and grab a &ldquo;Thread Safe&rdquo; version. I used PHP 5.5.31 VC11 x64 Thread Safe (since I needed 5.5 for my project and I am running on a x64 machine)</li>
		<li>Unzip the contents of the PHP .zip file into C:\Program Files\PHP</li>
		<li>Create C:\PHP</li>
		<li>Copy the file C:\Program Files\PHP\ext\php_openssl.dll to C:\PHP <span style="color:#FFA07A;">[ I reran these instructions with PHP7.1 and noticed that I need to place files under C:\PHP\ext now&nbsp;]</span></li>
		<li>Edit the files C:\Program Files\PHP\php.ini-development and C:\Program Files\PHP\php.ini-production in a text editor (like Notepad) and remove the semicolon (;) from line 876 (it should be extension=php_openssl.dll) <span style="color:#FFA07A;">[ thanks to La_Basse_Cour_BnB for pointing out that in later versions of PHP, the line number is now 907 ]</span></li>
		<li>Make a copy of C:\Program Files\PHP\php.ini-production and call it C:\Program Files\PHP\php.ini</li>
	</ol>
	</li>
	<li>Make PHP Available to Windows
	<ol style="list-style-type:lower-alpha;">
		<li>Right-click on the Start button (bottom left corner) and go to &ldquo;System&rdquo;</li>
		<li>Click on &ldquo;Advanced system settings&rdquo;</li>
		<li>Click on &ldquo;Environment Variables&hellip;&rdquo;</li>
		<li>Under &ldquo;System variables&rdquo; scroll down and highlight the variable &ldquo;Path&rdquo;</li>
		<li>Click &ldquo;Edit&hellip;&rdquo;</li>
		<li>Click &ldquo;New&rdquo;</li>
		<li>Create a new entry &ldquo;C:\Program Files\PHP&rdquo;</li>
		<li>Click &ldquo;New&rdquo;</li>
		<li>Create a new entry &ldquo;C:\PHP&rdquo;</li>
		<li>Click &ldquo;OK&rdquo;</li>
		<li>Under &ldquo;System variables&rdquo;, click &ldquo;New&hellip;&rdquo;</li>
		<li>For &ldquo;Variable name&rdquo; put &ldquo;OPENSSL_CONF&rdquo;</li>
		<li>For &ldquo;Variable value&rdquo; put &ldquo;C:\Program Files\PHP\extras\ssl\openssl.cnf&rdquo;</li>
	</ol>
	</li>
	<li>Install Visual C++ Redistributable for Visual Studio 2012 Update 4
	<ol style="list-style-type:lower-alpha;">
		<li>Use this link: <a href="https://www.microsoft.com/en-us/download/details.aspx?id=30679#">https://www.microsoft.com/en-us/download/details.aspx?id=30679#</a></li>
		<li>Download a copy of &ldquo;vcredist_x64.exe&rdquo; (or &ldquo;vcredist_x86.exe&rdquo; if you&rsquo;re running x86)</li>
		<li>Run the executable to install the missing .dll files you&rsquo;ll need for Composer</li>
	</ol>
	</li>
	<li>Download and Install Composer
	<ol style="list-style-type:lower-alpha;">
		<li>Simply go to <a href="http://getcomposer.org/download/">http://getcomposer.org/download/</a> and look for the Composer-Setup.exe link</li>
		<li>Install Composer</li>
    <li>add 'extension=php_fileinfo.dll' in php.ini
	</ol>
	</li>
</ol>
