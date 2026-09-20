# Política de privacidad — interbanking-mcp

*Última actualización: 20 de septiembre de 2026.*

## Lo corto

Este servidor corre en tu propia máquina, con tus propias credenciales, y habla únicamente con
los servicios de Interbanking. **No recolectamos nada, no mandamos nada a ningún lado y no tenemos
forma de ver tus cuentas ni tus movimientos.**

## Dónde corre

`interbanking-mcp` es un servidor MCP local: lo ejecuta tu cliente en tu equipo y se comunica por
entrada y salida estándar. No hay servidor nuestro en el medio. No hospedamos ningún servicio.

## Qué credenciales usa y de dónde salen

Se configuran como variables de entorno en tu equipo:

| Variable | Qué es |
|---|---|
| `IB_CLIENT_ID` | El identificador de tu aplicación en Interbanking |
| `IB_CLIENT_SECRET` | Su clave secreta |
| `IB_CUSTOMER_ID` | Tu identificador de cliente |
| `IB_REDIRECT_URL`, `IB_TOKEN_URL`, `IB_API_BASE_URL` | Los extremos del servicio |

**Ninguna de estas credenciales sale de tu equipo hacia nosotros.** Se usan solo para autenticarte
ante Interbanking, que es el único destinatario.

## A dónde se conecta

Únicamente a `auth.interbanking.com.ar` y `api-gw.interbanking.com.ar`. **A ningún otro lado.**
No hay telemetría, ni estadísticas de uso, ni servicio de errores, ni llamadas a terceros.

## Qué se guarda en disco

Nada. El servidor no escribe archivos: no guarda saldos, ni movimientos, ni un registro de lo que
consultaste. El token de acceso vive en memoria mientras el proceso corre y se pierde al cerrarlo.

## Solo lectura

Las cuatro herramientas son de consulta: cuentas, saldos, saldos históricos y movimientos.
**No hay ninguna que transfiera dinero, cargue un pago ni modifique nada.** Está declarado en el
código con las anotaciones del protocolo (`readOnlyHint`) y verificado por los tests del
repositorio.

## Lo que sí tenés que tener en cuenta

Esto es información financiera de tu empresa, así que vale decirlo con todas las letras: los
saldos y movimientos que devuelve este servidor **se los entrega a tu cliente MCP**, que en
general es un asistente de inteligencia artificial operado por otra empresa. Qué hace ese cliente
con esa información se rige por *su* política de privacidad, no por esta.

Antes de conectar cuentas reales, revisá las condiciones del cliente que vayas a usar. Es la única
parte del recorrido que este servidor no controla, y nos parece más honesto decirlo que omitirlo.

## Cambios

Si esto cambia, se actualiza este archivo y queda registrado en el historial del repositorio.

## Contacto

Por los issues del repositorio: <https://github.com/rje1974/interbanking-mcp/issues>

---

## Summary in English

`interbanking-mcp` is a local MCP server. It runs on the user's own machine over stdio, uses the
user's own Interbanking API credentials, and connects only to Interbanking's authentication and
API endpoints. No data is collected, transmitted to the author, or shared with third parties.
There is no telemetry and no hosted component. Nothing is written to disk: the access token is
held in memory for the life of the process. All four tools are read-only queries — none moves
money or modifies anything. Query results are returned to the user's MCP client, which may be an
AI assistant operated by another company and governed by its own privacy policy.
