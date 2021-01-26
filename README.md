# Help-HTTP-Delete


### Http Delete Not Allowed 

Com as configurações de publicação padrão do .NET Core, não é permitido usar o Request HTTP Delete. Se faz necessário atualizar o **web.config** (arquivo na pasta de publicação).   
Atualize para ficar da seguinte forma:
```
<?xml version="1.0" encoding="utf-8"?>
<configuration>
  <location path="." inheritInChildApplications="false">
    <system.webServer>		
		<modules>        
			<remove name="WebDAVModule" />    
		</modules>    
      <handlers>
        <add name="aspNetCore" path="*" verb="*" modules="AspNetCoreModuleV2" resourceType="Unspecified" />
      </handlers>
      <aspNetCore processPath="dotnet" arguments=".\Api.dll" stdoutLogEnabled="false" stdoutLogFile=".\logs\stdout" hostingModel="inprocess" />
    </system.webServer>
  </location>
</configuration>
```

O que adicionamos além do arquivo original está no seguinte trecho:
```
<modules>        
    <remove name="WebDAVModule" />    
</modules>    
```
<br>

Saiba mais sobre WebDav:
<https://www.cloudwards.net/what-is-webdav/>
