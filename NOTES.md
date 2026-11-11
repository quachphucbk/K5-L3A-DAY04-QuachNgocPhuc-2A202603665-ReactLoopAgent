# Ghi chú phân tích · Day 04

Họ và tên: Quách Ngọc Phúc
MSSV: 2A202603665

## 1. Case được chọn

- ID case: H1
- Câu trả lời của agent: "### Incident GitHub (h02n9572mx9y)\n\n- **Tên**: Incident with Actions\n- **Trạng thái**: Đã được giải quyết\n- **Thời gian bắt đầu**: 2026-11-04 17:40:33 (UTC)\n- **Thời gian giải quyết**: 2026-11-07 01:10:18 (UTC)\n- **Component**: Actions\n- **Cập nhật**:\n  1. **Đã giải quyết**: \"Please refer to the combined summary in this related incident: [link](https://www.githubstatus.com/incidents/xr3myzj7ms51)\" (2026-11-04 18:16:08)\n  2. **Theo dõi**: \"The degradation affecting Actions has been mitigated. We are monitoring to ensure stability.\" (2026-11-04 18:07:51)\n  3. **Đang điều tra**: \"We are investigating reports of degraded availability for Actions\" (2026-11-04 17:40:33)\n\n**Nguồn**: [GitHub Status](https://stspg.io/7pwv28hvkmz8)\n\n---\n\n### Incident Cloudflare (yaa0witbl2me)\n\n- **Tên**: Workers Builds Issues\n- **Trạng thái**: Đã được giải quyết\n- **Thời gian bắt đầu**: 2026-11-05 19:51:39 (UTC)\n- **Thời gian giải quyết**: 2026-11-05 20:20:10 (UTC)\n- **Component**: Workers Builds\n- **Cập nhật**:\n  1. **Đã giải quyết**: \"Queue times have returned to normal.\" (2026-11-05 20:20:10)\n  2. **Theo dõi**: \"Builds are being processed and we're working through backlog\" (2026-11-05 19:55:51)\n  3. **Đã nhận diện**: \"Cloudflare is aware of and investigating an issue with Cloudflare Workers Builds which potentially impacts multiple customers.\" (2026-11-05 19:51:39)\n\n**Nguồn**: [Cloudflare Status](https://www.cloudflarestatus.com/incidents/yaa0witbl2me)\n\n---\n\n### So sánh Incident và Phân tích Nguyên nhân\n\n1. **Thời gian bạn được ghi nhận**:\n   - GitHub: 2026-11-04\n   - Cloudflare: 2026-11-05\n   - **Kết luận**: Hai incident này không xảy ra cùng thời điểm.\n\n2. **Component**:\n   - GitHub liên quan đến \"Actions\"\n   - Cloudflare liên quan đến \"Workers Builds\"\n   - **Kết luận**: Không có sự chồng chéo về компонент.\n\n3. **Trạng thái**: Cả hai incident đều đã được giải quyết.\n\n### Kết luận\nDựa trên thông tin hiện có, không có bằng chứng nào cho thấy incident GitHub h02n9572mx9y gây ra lỗi cho dịch vụ Cloudflare yaa0witbl2me, cả về thời gian xảy ra và các component liên quan.",
- Điểm ở lần chạy 1: 60

## 2. Bằng chứng trong trace

Dán đoạn trace chứng minh lỗi và nêu nguyên nhân có thể xảy ra.

```text
"trace": [
          {
            "event": "model",
            "step": 1,
            "finish": "tool_calls"
          },
          {
            "event": "tool",
            "step": 1,
            "name": "get_incident_details",
            "call_id": "call_n1vHTC6oCKeBtfyZwKMWBLnp",
            "tool_call_id": "call_n1vHTC6oCKeBtfyZwKMWBLnp",
            "arguments": {
              "provider": "github",
              "incident_id": "h02n9572mx9y"
            },
            "result": {
              "ok": true,
              "provider": "github",
              "captured_at": "2026-11-09T03:50:47.065020+00:00",
              "id": "h02n9572mx9y",
              "name": "Incident with Actions",
              "status": "resolved",
              "created_at": "2026-11-04T17:40:33.675Z",
              "updated_at": "2026-11-07T01:10:18.506Z",
              "components": [
                "Actions"
              ],
              "updates": [
                {
                  "status": "resolved",
                  "created_at": "2026-11-04T18:16:08.361Z",
                  "body": "Please refer to the combined summary in this related incident: https://www.githubstatus.com/incidents/xr3myzj7ms51",
                  "truncated": false
                },
                {
                  "status": "monitoring",
                  "created_at": "2026-11-04T18:07:51.114Z",
                  "body": "The degradation affecting Actions has been mitigated. We are monitoring to ensure stability.",
                  "truncated": false
                },
                {
                  "status": "investigating",
                  "created_at": "2026-11-04T17:40:33.887Z",
                  "body": "We are investigating reports of degraded availability for Actions",
                  "truncated": false
                }
              ],
              "updates_total": 4,
              "url": "https://stspg.io/7pwv28hvkmz8"
            }
          },
          {
            "event": "tool",
            "step": 1,
            "name": "get_incident_details",
            "call_id": "call_2SI8qBe1homLewdE9e8qkXd7",
            "tool_call_id": "call_2SI8qBe1homLewdE9e8qkXd7",
            "arguments": {
              "provider": "cloudflare",
              "incident_id": "yaa0witbl2me"
            },
            "result": {
              "ok": true,
              "provider": "cloudflare",
              "captured_at": "2026-11-09T03:50:47.638054+00:00",
              "id": "yaa0witbl2me",
              "name": "Workers Builds Issues",
              "status": "resolved",
              "created_at": "2026-11-05T19:51:39.176Z",
              "updated_at": "2026-11-05T20:20:10.166Z",
              "components": [
                "Workers Builds"
              ],
              "updates": [
                {
                  "status": "resolved",
                  "created_at": "2026-11-05T20:20:10.166Z",
                  "body": "Queue times have returned to normal.",
                  "truncated": false
                },
                {
                  "status": "monitoring",
                  "created_at": "2026-11-05T19:55:51.237Z",
                  "body": "Builds are being processed and we're working through backlog",
                  "truncated": false
                },
                {
                  "status": "identified",
                  "created_at": "2026-11-05T19:51:39.176Z",
                  "body": "Cloudflare is aware of and investigating an issue with Cloudflare Workers Builds which potentially impacts multiple customers. Further detail will be provided as more information becomes available.",
                  "truncated": false
                }
              ],
              "updates_total": 3,
              "url": "https://www.cloudflarestatus.com/incidents/yaa0witbl2me"
            }
          },
          {
            "event": "model",
            "step": 2,
            "finish": "stop"
          }
        ]
```  
Nguyên nhân có thể xảy ra:  
- Agent chỉ chạy 1 model step duy nhất:  
   Step 1: get_incident_details của (github, h02n9572mx9y) và (cloudflare, yaa0witbl2me)  
   Step 2: dừng và trả lời  
Điều này khiến agent không follow link, kết quả h02n9572mx9y có update Please refer to the combined summary in this related incident: https://www.githubstatus.com/incidents/xr3myzj7ms51 agent không gọi thêm get_incident_details(github, xr3myzj7ms51) nên bỏ lỡ nguyên nhân và ảnh hưởng thực sự của GitHub.

## 3. Thay đổi đã thực hiện

- Sửa gì, ở đâu: Sửa SYSTEM_PROMPT trong agent.py
- Vì sao chọn thay đổi này: Định nghĩa rõ ràng các bước cho agent khi thực hiện điều tra incident để tránh bỏ lỡ nguyên nhân thực sự.

## 4. So sánh hai lần chạy

| Chỉ số | `eval_before.json` | `eval_after.json` |
|---|---|---|
| Điểm tổng | 80.82|82.5  |
| Điểm case đã chọn |  60|100  |
| Số model calls |  2|  4|
| Token, chi phí nếu có |  input_tokens: 1292, output_tokens:  765 => Chi phí: 1.292 * 0.00015 + 0.765 * 0.000075 = 0. 00025118|  input_tokens: 4204, output_tokens:744 => Chi phí: 4.204 * 0.00015 + 0.744 * 0.000075 =0.0006864  |

- Lỗi đã giải quyết: Nhiều bước và dữ liệu dài:** H1. Agent không gọi tiếp khi thấy incident liên quan.
- Lỗi còn lại hoặc mới xuất hiện: Nguồn và scope, Partial failure và prompt injection, Yêu cầu sai hoặc ngoài luồng

## 5. Giới hạn

Nêu giới hạn của điểm judge, của snapshot và của việc chỉ chạy một lần mỗi phiên bản.
- Điểm judge: LLM judge có thể chấm sai, bỏ sót bằng chứng hoặc đánh giá không nhất quán. Cần đối chiếu điểm với expected, câu trả lời và trace thay vì chỉ nhìn điểm.  
- Snapshot: dữ liệu chỉ phản ánh thời điểm thu thập, không chứng minh trạng thái dịch vụ hiện tại. Tool chỉ tìm trong 50 incident gần nhất, trả tối đa 5 incident khớp và có thể lược bớt updates hoặc cắt nội dung. Vì vậy, không tìm thấy không có nghĩa là không có sự cố; dữ liệu cũng chưa đủ để kết luận incident gây ra lỗi của người dùng.
- Chỉ chạy 1 lần mỗi phiên bản: không chứng minh độ ổn định, 1 lần chạy eval không đủ để kết luận prompt/agent đã cải thiện. LLM có tính ngẫu nhiên, lần sau có thể cho kết quả khác. Điểm tăng/giảm có thể do ngẫu nhiên của model chứ không phải do thay đổi thực sự tốt/xấu.
