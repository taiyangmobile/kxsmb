KxSMB is objective-c wrapper for libsmbclient lib. 
===========================================

For now KxSMB supports a limited set of SMB operations.
It mostly was designed for browsing local net and retrieving files.

### Build instructions:

First you need download, configure and build [samba](http://www.samba.org).
For this open console and type in
	
	cd kxsmb	
	--新增以下代码 用于安装autoconf
	curl -O http://mirrors.kernel.org/gnu/autoconf/autoconf-2.65.tar.gz
	tar -xzvf autoconf-2.65.tar.gz
	cd autoconf-2.65
	./configure –prefix=/usr/local
	make
	sudo make install
	cd ..
	curl -O http://mirrors.kernel.org/gnu/automake/automake-1.11.tar.gz
	tar xzvf automake-1.11.tar.gz
	cd automake-1.11
	./configure –prefix=/usr/local
	make
	sudo make install
	cd ..
	curl -O http://mirrors.kernel.org/gnu/libtool/libtool-2.2.6b.tar.gz
	tar xzvf libtool-2.2.6b.tar.gz
	cd libtool-2.2.6b
	./configure –prefix=/usr/local
	make
	sudo make install
	--然后在运行rake就一次可以通过了
	rake
	
### Usage

1. Drop files from kxsmb/libs folder in your project.
2. Add libs: libz.dylib, libresolv.dylib and liconv.dylib.

Fetching a folder content:

	NSArray *items = [[KxSMBProvider sharedSmbProvider] fetchAtPath: @"smb://server/share/"];

Reading a file:

	KxSMBItemFile *file = [[KxSMBProvider sharedSmbProvider] fetchAtPath: @"smb://server/share/file"];
	NSData *data = [file readDataToEndOfFile];

Look at kxSMBSample demo project as example of using.

### Requirements

at least iOS 5.0 and Xcode 4.5.0

### License

kxsmb is open source and covered by a standard 2-clause BSD license. See the LICENSE file for more info.

[Samba](http://www.samba.org) is [Free Software](http://www.gnu.org/philosophy/free-sw.html) licensed under the [GNU General Public License](http://www.samba.org/samba/docs/GPL.html).

### Feedback

Tweet me — [@kolyvan_ru](http://twitter.com/kolyvan_ru).
