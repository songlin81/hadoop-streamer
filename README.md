# hadoop
 
### Installation
	H:\>java -version
	java version "1.8.0_261"
	Java(TM) SE Runtime Environment (build 1.8.0_261-b12)
	Java HotSpot(TM) 64-Bit Server VM (build 25.261-b12, mixed mode)

	H:\>echo %JAVA_HOME%
	C:\Program Files\Java\jdk1.8.0_261

	C:\repo\hadoop\hadoop-2.7.7\etc\hadoop\hadoop-env.cmd
		--> set JAVA_HOME=C:\PROGRA~1\Java\jdk1.8.0_261

### Create directory
	C:\repo\hadoop\hadoop-2.7.7\data\dfs\namenode
	C:\repo\hadoop\hadoop-2.7.7\data\dfs\datanode

### Configuration
	C:\repo\hadoop\hadoop-2.7.7\etc\hadoop\core-site.xml
	C:\repo\hadoop\hadoop-2.7.7\etc\hadoop\hdfs-site.xml
	C:\repo\hadoop\hadoop-2.7.7\etc\hadoop\mapred-site.xml
	C:\repo\hadoop\hadoop-2.7.7\etc\hadoop\yarn-site.xml

### Replace LF with CRLF for below:
	C:\repo\hadoop\hadoop-2.7.7\etc\hadoop\yarn-env.sh
	C:\repo\hadoop\hadoop-2.7.7\bin\yarn.cmd
	C:\repo\hadoop\hadoop-2.7.7\sbin\start-yarn.sh

### Format
	C:\repo\hadoop\hadoop-2.7.7\bin>hdfs namenode -format
		--> Re-format filesystem in Storage Directory C:\repo\hadoop\hadoop-2.7.7\data\dfs\namenode ? (Y or N)
		--> Y
	or
	./hdfs namenode -format -clusterId CID-07bfc31d-0d36-41e5-8a3a-5fee059787af
	
### Script
	c:\repo\hadoop\hadoop-2.7.7\sbin>start-all.cmd
	This script is Deprecated. Instead use start-dfs.cmd and start-yarn.cmd
	starting yarn daemons

	c:\repo\hadoop\hadoop-2.7.7\sbin>jps
	11904 DataNode
	12464 ResourceManager
	3396 NameNode
	16040 Jps
	14476 NodeManager
	
### Web UI 
	http://localhost:50070/dfshealth.html	
	http://localhost:8088/cluster
		
### Execute
	C:\repo\hadoop\hadoop-2.7.7\sbin>hadoop fs -mkdir /input
	C:\repo\hadoop\hadoop-2.7.7\bin>hdfs dfs -copyFromLocal C:\repo\hadoop\file1.txt /input
	C:\repo\hadoop\hadoop-2.7.7\bin>hdfs dfs -ls /input
		Found 1 items
		-rw-r--r--   1 v0cn140 supergroup         55 2020-10-02 11:47 /input/file1.txt
	C:\repo\hadoop\hadoop-2.7.7\bin>yarn jar ../share/hadoop/mapreduce/hadoop-mapreduce-examples-2.7.7.jar wordcount /input /output
	C:\repo\hadoop\hadoop-2.7.7\bin>hdfs dfs -cat /output/*
		Example 1
		Hadoop  2
		Install 1
		Mapreduce       1
		Run     1
		Wordcount       1

	# delete output and re-run above
	C:\repo\hadoop\hadoop-2.7.7\bin>hadoop fs -rm -r -f /output