# Kubernetes-KEDA-AzureQueueStorage_ContagemAcessos
Objetos para Deployment de um Worker Service (contagem de acessos) no Kubernetes utilizando KEDA, Helm, Azure Queue Storage e um Worker criado com .NET 7. Foi definido 1 exemplo para ScaledObject (com cooldownPeriod).

Worker Service para consumo de **mensagens vinculadas a uma fila do Azure Queue Storage** (imagem **renatogroffe/workercontagem-dotnet7-azurequeuestorage**), com **monitoramento via Application Insights** - é justamente esta aplicação que será escalada via **KEDA**:

**https://github.com/renatogroffe/DotNet7-WorkerService-AzureQueueStorage-Sql-AppInsights_ContagemAcessos**

Projeto que serviu de base para o **envio de mensagens a uma fila do Azure Queue Storage** (imagem **renatogroffe/apicontagem-dotnet7-azurequeuestorage**):

**https://github.com/renatogroffe/ASPNETCore7-REST_API-AzureQueueStorage_ContagemAcessos**

No arquivo **keda-instalacao&sdot;sh** estão as instruções para instalação do KEDA **(Kubernetes Event-driven Autoscaling)** em um **cluster Kubernetes**.

Para os testes de carga que escalam a aplicação utilizei o pacote npm [**loadtest**](https://www.npmjs.com/package/loadtest). O exemplo a seguir procerá com o envio de **3 mil requisições**, simulando **50 usuários concorrentes**:

**loadtest -c 50 -n 3000 -k** ***ENDPOINT***