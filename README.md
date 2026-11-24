# CP2-SaludIntegral-GrupoD

**Componente Práctico 2 (CP2)**  
**Proyecto:** Sistema de historia clínica electrónica "SaludIntegral"  
**Grupo:** D

## Integrantes

| Nombre completo | Usuario |
| :--- | :--- |
| Angulo Pilozo Santiago Alejandro | `sangulop2` |
| Guaman Vega John Jairo | `jguamanv6` |
| Ballesteros Chichande Allan Josue | `allanballesteros-oss` |
| Bajaña Asqui Elkin Armando | `ebajanaa7` |
| Acero Espinoza Daniel Sebastian | `sebasacero-cmd` |
| Arguello Muñoz Joel Santiago | `joelargu` |
  
## Introducción
Las historias clínicas electrónicas facilitan la atención médica, pero concentran datos de salud sensibles que requieren una protección rigurosa. Este trabajo analiza el sistema "SaludIntegral", una red de centros médicos donde todo el personal podía consultar cualquier expediente sin distinción de roles y sin un registro de accesos, lo que comprometía la confidencialidad exigida por la Ley Orgánica de Protección de Datos Personales (LOPDP). Para solucionarlo, se plantea un sistema que limite el acceso según la función de cada usuario y registre cada consulta con su motivo. El documento presenta los requisitos funcionales y no funcionales, junto con sus casos de prueba y resultados esperados, además del registro de colaboradores del proyecto.

## Tabla de requisitos y casos de prueba
| ID | Tipo | Descripción del requisito | Caso de prueba propuesto | Resultado esperado |
| :--- | :--- | :--- | :--- | :--- |
| RF-01 | Funcional | El sistema debe permitir configurar permisos por rol institucional (médico, enfermero, recepcionista y administrativo), mostrando a cada usuario únicamente los módulos correspondientes a sus funciones. | CP-01: Iniciar sesión con una cuenta configurada con el rol Recepcionista y navegar por el menú principal hacia el expediente de un paciente. | El sistema muestra únicamente el módulo de gestión de citas y datos generales, manteniendo ocultos y bloqueados los módulos de diagnósticos médicos y resultados de laboratorio. |
| RF-02 | Funcional | El sistema debe registrar automáticamente una bitácora de auditoría por cada consulta a un expediente, guardando usuario, rol, paciente, fecha, hora y motivo obligatorio. | CP-02: Iniciar sesión con un usuario de rol Médico, abrir la historia clínica de un paciente ingresando el motivo "Control médico rutinario" y luego revisar el panel de bitácora de auditoría. | El sistema registra automáticamente una nueva entrada con el ID del médico, su rol, la cédula del paciente, la fecha, la hora exacta y el motivo ingresado. |
| RF-03 | Funcional | El sistema debe permitir al personal clínico autorizado registrar, actualizar y consultar diagnósticos, exámenes, recetas y citas del paciente mediante su número de cédula. | CP-03: Buscar un paciente mediante su número de cédula válido desde la cuenta del médico asignado a su atención, registrar un nuevo diagnóstico junto con una receta médica y volver a consultar el expediente. | El sistema recupera el historial del paciente, almacena el nuevo diagnóstico y la receta, y los despliega correctamente en la historia clínica electrónica. |
| RNF-01 | No funcional | El sistema debe restringir el acceso a la información clínica según el rol del usuario (médico, enfermero, administrativo) y exigir autenticación con usuario y contraseña. | CP-04: Iniciar sesión con credenciales válidas de un usuario con rol administrativo e intentar acceder al módulo de edición de diagnósticos médicos. | El sistema valida la sesión, bloquea el acceso al módulo clínico restringido y muestra el mensaje: "Acceso denegado: su rol no tiene permisos para esta sección". |
| RNF-02 | No funcional | El sistema debe responder a las consultas de historiales clínicos en un máximo de 3 segundos, con hasta 100 usuarios conectados al mismo tiempo. | CP-05: Simular una prueba de carga con 100 usuarios concurrentes realizando búsquedas simultáneas de historiales clínicos mediante número de cédula. | El sistema procesa todas las solicitudes sin caídas y devuelve cada historial clínico en pantalla en un tiempo igual o inferior a 3 segundos. |
  
