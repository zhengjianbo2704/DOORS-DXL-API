# DOORS-DXL-API

1.准备资料：
	1) doors 安装客户端服务端
	2) doors客户端目录中api/目录下的文件（开发C# java 接口dll需要）
	3) doors客户端bin/目录下的 dll  lib文件（开发C# java 接口dll需要）
	4) java或者C#开发环境.
	5) 开发简易说明：api/api.txt 
2.接口原理:
	1) doors提供了对外接口服务：
		evalTop_ "initDXLServer server 5093" //v1服务端口功能 因为简单，故不适用
		evalTop_ "initDXLServerV2 server 5094" //v2端口功能比较强大
	2) 根据提供的dll api txt 开发dll接口。
	3) 读取数据示意图： 
		
		  DOORS SERVER  <-> DOORS CLIENT <-->（initDXLServerV2 server 5094）->  C#/JAVA(DLL接口(开发))  ----->>> 输出端
								|																|
								↕ DXL(执行)生成文件至											↕(C#/JAVA功能读取XML文件)
								|																↕
						----DISK(D:盘)-----														↕	
						----（DXL生成的文件XML等）-----------------------------------------------
	
	4) DOORS CLIENT(执行DXL 启动serverV2:5094 )
	5) JAVA/C# 调用5094端口发送需执行的DXL文件：（发送的dxl文件是需要执行的操作）