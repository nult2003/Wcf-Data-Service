# Wcf-Data-Service
Request entity too large error(413) in WCF on WCF Data service

https://stackoverflow.com/questions/5918749/how-to-work-around-the-default-message-size-limit-in-wcf-data-service?answertab=active#tab-top
<system.serviceModel>
 <serviceHostingEnvironment aspNetCompatibilityEnabled="true"/>
 <services>
     <!-- The name of the service -->
     <service name="PhotoService.PhotoData">
         <!--you can leave the address blank or specify your end point URI-->
         <endpoint binding="webHttpBinding" 
           bindingConfiguration="higherMessageSize" 
           contract="System.Data.Services.IRequestHandler"></endpoint>
     </service>
 </services>
 <bindings>
     <webHttpBinding>
         <!-- configure the maxReceivedMessageSize value to suit the max size of 
                  the request (in bytes) you want the service to receive-->
         <binding name="higherMessageSize" transferMode="Streamed"  
          maxReceivedMessageSize="2147483647"/>
     </webHttpBinding>
 </bindings>
