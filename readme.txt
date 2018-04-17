1、修改generatorConfig.xml文件中数据库信息，生成的包名、指定数据库中的表
2、执行GeneratorSqlmap.java的main方法生成mapper和pojo两个包 
3、将生成的两个包copy到项目的src/main/java包下


注意：因为生成的TableNameMapper.xml文件也在mapper包下，所以copy过去之后不在src/main/resources包下，因此项目无法找到TableNameMapper.xml文件
解决办法：在项目的pom.xml文件中添加如下配置,让项目扫描src/main/java下的配置文件（mapper.xml）

<build>
	<resources>
            <resource>
                <directory>src/main/java</directory>
                <includes>
                    <include>**/*.properties</include>
                    <include>**/*.xml</include>
                </includes>
                <filtering>false</filtering>
            </resource>
            <resource>
                <directory>src/main/resources</directory>
                <includes>
                    <include>**/*.properties</include>
                    <include>**/*.xml</include>
                </includes>
                <filtering>false</filtering>
            </resource>
	</resources>
</build>
